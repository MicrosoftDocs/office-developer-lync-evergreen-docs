---
title: Set up the UCWA event channel to receive incoming notifications
TOCTitle: Set up the event channel to receive incoming notifications
ms:assetid: 05cf010f-77c3-41b7-9dcd-037479b2f004
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn683882(v=office.15)
ms:contentKeyID: 62183413
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Set up the UCWA event channel to receive incoming notifications

Learn how to set up an event channel in your Microsoft Unified Communications Web API 1.0 Windows Store app in C\#/XAML and XML. Setting up the event channel is necessary to enable many UCWA 1.0 features, including receiving presence updates of contacts, conducting instant messaging, audio/video calls or online meetings, and so on.


_**Applies to:** Lync 2010 | Lync 2013 | Lync Server 2013_

**In this article**  
Set up the event channel  
Start and stop the event loop  
Initialize a pending HTTP GET request  
Process PGET responses  
Hook up the event channel  
Additional resources  

The UCWA 1.0 event channel allows a UCWA 1.0 application to receive application data, including call invitations, whenever the data are available. Although the application can poll the server to receive many kinds of the application data, such as the user info about the local user, it must rely on the event channel to enable the user to receive any incoming call. You can build your application in such a way that the event channel is the sole mechanism to receive application data.

In a UCWA 1.0 event channel is a persistent GET request, also referred to as P-GET. Once properly initialized, a UCWA 1.0 application starts the event channel by submitting an HTTP GET request against the [events](http://ucwa.lync.com/documentation/resources-events) resource available from the signed-in [application](http://ucwa.lync.com/documentation/resources-application). Upon receiving this GET request, UCWA 1.0 holds the response to the GET request until some events occurred or the operation is timed out or becomes invalid. A successful response contains the occurred events as well as the URI of the next event notification. To keep the event channel open, the application must immediately submit a new HTTP GET request against the new event URI contained in the response and then wait for its response. The process continues until the event channel is no longer needed, such as when the application exits. On the other hand, an unsuccessful response reports an error condition, including time-out message. Depending on the error conditions, the application can choose to restart, repair or close the event channel.

Programmatically, setting up the even channel in an application, thus, involves the following steps.

1.  Parse the event URI from a signed-in application resource.

2.  Submit an HTTP GET request against the event URI

3.  Wait for the response from the HTTP GET request.

4.  For a successful response, parse the next event URI and dispatch event data for any registered event handlers. Repeat from Step 2 using the new event URI.

5.  For other responses, repair, restart or close the event channel.

One way to implement the above steps involves executing the HTTP GET requests and responses synchronously in a separate thread. The details of this implementation and those of the individual steps are the topics of the following sections.

## Set up the event channel

We will continue from our [Introductory UCWA Windows Store application](http://code.msdn.microsoft.com/lync/create-a-ucwa-windows-2c48d3f9) to add the event channel features. You can follow the [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md) article to create the Visual Studio project and to include necessary application components.

To set up the event channel and integrate it with other parts of our UCWA 1.0 application, let us first encapsulate the event channel in public-scoped class named UcwaAppEventChannel. For this, add the following class definition to the Visual Studio solution.

``` csharp
using System;
using System.Linq;
using System.Net;
using System.Threading.Tasks;

namespace WinStoreUcwaAppEvents
{
    public sealed class UcwaAppEventChannel
    {
        string url;

        public UcwaAppTransport Transport { get; private set; }
        public UcwaAppEventNotificationsReceivedEventHandler OnEventNotificationsReceived;
        public UcwaAppEventChannelClosedEventHandler OnEventChannelClosed;
        public UcwaAppProgressReportEventHandler OnProgressReported;
        public UcwaAppErrorReportEventHandler OnErrorReported;

        public UcwaAppEventChannel(string channelUri, UcwaAppTransport transport) 
        {
            this.Transport = transport;
            this.url = channelUri;
        }
    }
}
```

In the above class definition, the event channel class is created with two external inputs: channelUri and transport. The channelUri holds the Uri of the events resource made available from a signed-in application resource. transport is an instance of the UcwaAppTransport class encapsulating the HTTP operations. Both are cached as the respective class variables. In addition, four delegates are exposed on the class to dispatch event channel data and states to registered event handlers. The OnEventNotificationsReceived delegate will be used to forward the event channel data. The OnEventChannelClosed, OnProgressReported, OnErrorReported delegates are used to dispatch the states of the event channel. Examples of the event handlers are given below.

## Start and stop the event loop

Add the following member definition to the UcwaAppEventChannel class to open the event channel by starting a loop to poll the [events](http://ucwa.lync.com/documentation/resources-events) resource in a separate thread from the application’s main thread.

``` csharp
        Windows.Foundation.IAsyncAction workItem;
        public void Start( )
        {
            var uri = this.url;
            UcwaAppOperationResult result;

            workItem = Windows.System.Threading.ThreadPool.RunAsync(
                async ( workItemHandler) => 
                {
                    while (!string.IsNullOrWhiteSpace(uri))
                    {
                        if (workItem.Status == Windows.Foundation.AsyncStatus.Canceled)
                            break;

                        // Make pending-Get request
                        result = await this.Transport.GetResourceAsync(uri);
                        if (result.StatusCode == HttpStatusCode.OK)
                        {
                            uri = GetNextEventUri(result.Resource);
                            HandleEvent(result.Resource);
                        }
                        else
                        {
                            HandleException(result);
                        }                                                    
                    }
                },
                Windows.System.Threading.WorkItemPriority.Normal
            );
            workItem.Completed += new Windows.Foundation.AsyncActionCompletedHandler(
                (Windows.Foundation.IAsyncAction source, Windows.Foundation.AsyncStatus status) =>
                {
                    if (workItem.Status == Windows.Foundation.AsyncStatus.Canceled)
                        return;

                    if (OnEventChannelClosed != null) OnEventChannelClosed(status);
                });

        }
```

Here, GetResourceAsync(uri) is called to perform an HTTP GET request. Using the async/await programming pattern, the call is blocked until the server has events to return. Care must be taken to ensure that the call is not prematurely time out. For details, see [Initialize a pending HTTP GET request](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md) in this article.

When the server returns event data in a response, the next event Uri is extracted from the returned [events](http://ucwa.lync.com/documentation/resources-events) resource for the event loop to continue. In the meantime, HandleEvents is called to forward event data to registered event handlers for processing. If an unsuccessful response is returned, HandleException is called. The detailed discussions of these methods are the topics of the [Process PGET responses](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md) section.

To stop or cancel the running thread for events, add the following member definition to the UcwaAppEventChannel class to break the event loop.

``` csharp
        public void Stop()
        {
            if (workItem != null && workItem.Status == Windows.Foundation.AsyncStatus.Started)
            {
                workItem.Cancel();
            }
        }
```

When the Stop() is called, the event channel will exit from the event loop. The application will then not receive any more event notifications.

## Initialize a pending HTTP GET request

In a pending HTTP GET request, UCWA may hold the operation longer than the default timeout value set by the underlying [HttpClient](http://msdn.microsoft.com/en-us/library/system.net.http.httpclient\(v=vs.118\).aspx) class. When this happens, the [GetAsync](http://msdn.microsoft.com/en-us/library/system.net.http.httpclient.getasync\(v=vs.118\).aspx) and the related methods will raise [TaskCanceledException](http://msdn.microsoft.com/en-us/library/system.threading.tasks.taskcanceledexception\(v=vs.110\).aspx). To prevent this from happening, we change the [Timeout](http://msdn.microsoft.com/en-us/library/system.net.http.httpclient.timeout\(v=vs.118\).aspx) value to 30 minutes on **HttpClient**. This can be done when the UcwaAppTransport class is initialized. This is illustrated as follows in one of the overloaded Initialize methods.

``` csharp
        public void Initialize(HttpHeaderValueCollection<MediaTypeWithQualityHeaderValue> accept, AuthenticationHeaderValue authorization, Uri baseAddress)
        {
            Client = new HttpClient();
            Client.Timeout = new TimeSpan(0, 30, 0);  // initialize the app timeout to be 30 minutes.
            this.SetAccept(accept);
            if (baseAddress != null) this.Client.BaseAddress = baseAddress; // must be set before any request is made
            if (authorization != null)
            {
                this.SetAuthorization(authorization);
                this.Client.DefaultRequestHeaders.Authorization = authorization;
            }
        }
```

When a UCWA application remains idle for some time beyond the preconfigured timeout period, UCWA will act to reclaim the application. To keep the application live when long idle time is expected, as with a UCWA event channel, the application can send to UCWA a [reportMyActivity](http://ucwa.lync.com/documentation/resources-reportmyactivity) request periodically.

This can be done by setting a timer that submits an HTTP PUT request every 4 minutes or so. To enable this, add the following code snippet to the UcwaApp class after the [me](http://ucwa.lync.com/documentation/resources-me) resource is successfully obtained.

``` csharp
                // Set up a timer to post on reportMyActivity every four minutes
                timer = new Timer((e) =>
                    {ReportMyActivity(this.ApplicationResource.GetEmbeddedResource("me").GetLinkUri("reportMyActivity"));}, 
                    null, 
                    new TimeSpan(0, 0, 0), 
                    new TimeSpan(0, 4, 0)
                );
```

It is assumed that the class variable timer is already declared in the UcwaApp class.

## Process PGET responses

Processing the response from a PGET request involves handling the event data, including extracting the next event Uri, when the request succeeds and handling the exception when the request fails. The following sample implementation of the event handling routine is shown as an illustration.

``` csharp
        private void HandleEvent(UcwaResource resource)
        {
            if (OnEventNotificationsReceived != null)
                OnEventNotificationsReceived(new UcwaEventsData(resource.OuterXml));
        }
        private string GetNextEventUri(UcwaResource resource)
        {
            try
            {
                if (resource.LinkNames.Contains("resync"))
                    return resource.GetLinkUri("resync");
                if (resource.LinkNames.Contains("resume"))
                    return resource.GetLinkUri("resume");
                if (resource.LinkNames.Contains("next"))
                    return resource.GetLinkUri("next");
                return null;
            }
            catch { return null; }
        }
```

Here, processing of event data is deferred to upstream event handlers that are registered with the event channel. The next event Uri includes that ("resync") to be obtained after the client is resynchronized with the server or that ("resume") to be continued from a specified address.

The following sample implementation illustrates what kind of error conditions one may encounter.

``` csharp
        private void HandleException(UcwaAppOperationResult result)
        {
            switch (result.StatusCode)
            {
                case HttpStatusCode.RequestTimeout:
                    // server timed out.
                    stopPGet = true;
                    TaskCanceledException tcex = result.Exception as TaskCanceledException;
                    ReportError(tcex.Message);
                    break;
                case HttpStatusCode.Conflict:
                    // HttpStatusCode.Conflict: duped ack Ids
                    stopPGet = true;
                    ReportError(result.StatusCode.ToString());
                    break;
                case HttpStatusCode.NotFound:
                    // HttpStatusCode.NotFound: server app not exists
                    stopPGet = true;
                    ReportError(result.StatusCode.ToString());
                    break;
                default:
                    stopPGet = true;
                    ReportError(result.Exception.Message);
                    break;
            }
            This.Stop();
        }
        private void ReportError(HttpStatusCode statusCode)
        {
            if (OnErrorReported != null)
                OnErrorReported(new Exception(statusCode.ToString()));
        }
        private void ReportError(string msg)
        {
            if (OnErrorReported != null)
                OnErrorReported(new Exception(msg));
        }
```

## Hook up the event channel

To hook up the event channel with the rest of your UCWA 1.0 application, add the following code snippets after the application resource is created and returned. A successfully created application resource is required in order to obtain the Uri of the events resource to start the event channel. In our example, this takes place in the UcwaApp class

``` csharp
                // Setup and start event channel
                var eventsUri = this.ApplicationResource.GetLinkUri("events");
                this.EventChannel = new UcwaAppEventChannel(eventsUri, this.Transport);
                this.EventChannel.OnEventNotificationsReceived += EventChannel_OnEventNotificationsReceived;
                this.EventChannel.OnErrorReported += EventChannel_OnErrorReported;
                this.EventChannel.OnEventChannelClosed += EventChannel_OnEventChannelClosed;
                this.EventChannel.OnProgressReported += EventChannel_OnProgressReported;   
                this.EventChannel.Start();
                UcwaAppUtils.ReportProgress(OnProgressReported, "Event channel started on " + eventsUri);
```

Examples of the specified event handlers are shown as follows:

``` csharp
        async void EventChannel_OnEventNotificationsReceived(UcwaEventsData events)
        {
            UcwaEventsData eventsData = events as UcwaEventsData;
            if (eventsData == null)
                return;
            if (this.OnEventNotificationsReceived != null)
                await UcwaAppUtils.DispatchEventToUI(CoreDispatcherPriority.Normal,
                    new DispatchedHandler(() => { this.OnEventNotificationsReceived(eventsData); }));

            foreach (var sender in eventsData.SenderNames)
            {
                if (OnEventsReceived != null)
                    await UcwaAppUtils.DispatchEventToUI(CoreDispatcherPriority.Normal,
                        new DispatchedHandler(() => { OnEventsReceived(sender, eventsData.GetEventsBySender(sender)); }));
            }
        }
        bool restartEventChannel = false;
        async void EventChannel_OnErrorReported(Exception e)
        {
            // connection interrupted.
            // report error and restart the event channel
            if (OnErrorReported != null)
                await UcwaAppUtils.DispatchEventToUI(
                    CoreDispatcherPriority.Normal, 
                    new DispatchedHandler(() => { OnErrorReported(e); }));
            this.restartEventChannel = true;
            
        }
        async void EventChannel_OnEventChannelClosed(Windows.Foundation.AsyncStatus status)
        {
            if (OnEventChannelTerminated != null)
                await UcwaAppUtils.DispatchEventToUI(CoreDispatcherPriority.Normal,
                    new DispatchedHandler(() => { OnEventChannelTerminated(status); }));
            if (this.restartEventChannel)
                this.EventChannel.Start();
        }
        async void EventChannel_OnProgressReported(string msg, HttpStatusCode status)
        {
            if (OnProgressReported != null)
                await UcwaAppUtils.DispatchEventToUI(
                    CoreDispatcherPriority.Normal,
                    new DispatchedHandler(() => { OnProgressReported(msg, status); }));
        }
```

Here, it is assumed that the upstream event handler is registered from a UI thread that will display the error messages and other warnings to the user.

## Additional resources

  - [Getting Started](http://ucwa.lync.com/documentation/getting-started) with UCWA 1.0.

  - UCWA 1.0[Event Channel Details](http://ucwa.lync.com/documentation/gettingstarted-events).

  - UCWA 1.0[events](http://ucwa.lync.com/documentation/resources-events) resource reference page.

  - [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md). More additional resources are listed therein.

  - [Download the Visual Studio solution of the accompanying sample code](http://code.msdn.microsoft.com/lync-2013-open-an-event-d4b6cb62).

