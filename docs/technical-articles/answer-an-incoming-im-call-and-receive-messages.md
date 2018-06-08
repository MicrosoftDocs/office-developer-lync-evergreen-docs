---
title: Answer an incoming IM call and receive messages
TOCTitle: Answer an incoming IM call and receive messages
ms:assetid: 5025b186-4011-47e7-acc3-34ab8994bff8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn771762(v=office.15)
ms:contentKeyID: 62554469
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xml
---

# Answer an incoming IM call and receive messages

Learn how to accept incoming IM calls from a contact and to receive incoming IM messages from the remote participant in your Microsoft Unified Communications Web API 1.0 Windows Store app in C\#/XMAL and XML.


**In this article**  
Before you start  
Overview of the process for answering incoming calls  
Get ready to answer a call  
Answer the incoming call  
Receive incoming IM messages  
Parse received IM messages  
Additional resources  

Just like when you [make an outgoing call](making-an-outgoing-im-call-and-sending-messages.md), to accept incoming instant messaging (IM) calls, you need to handle appropriate event notifications. In this article, you’ll learn what basic events to catch and how to process them.

In UCWA, to answer an IM call, you submit a POST request on the [accept](http://ucwa.skype.com/documentation/resources-accept) resource after receiving a notification of an incoming [messagingInvitation](http://ucwa.skype.com/documentation/resources-messaginginvitation)-started event. This will change the **messagingInvitation** state from Connecting to Connected. As a result, the underlying **conversation** state will also change from Connecting to Connected.

After the call is connected, to receive messages from other participants, you must capture the [message](http://ucwa.skype.com/documentation/resource-message) event that originated from the conversation and parse the event data. The message that you retrieve can be a base64-encoded HTML or a URL-encoded plain text.

## Before you start

Complete the following tasks before you start the process described in this article:

  - Create your [application](http://ucwa.skype.com/documentation/resources-application).

  - Start the [event channel](http://ucwa.skype.com/documentation/programmingconcepts-events).

  - Sign in to UCWA.

  - Turn on the [makeMeAvailable](http://ucwa.skype.com/documentation/resources-makemeavailable) option for the application to receive incoming notifications and incoming IM messages.

  - Retrieve the updated **application** resource.

For more information, see [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md) and [Set up the UCWA event channel to receive incoming notifications](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md).

## Overview of the process for answering incoming calls

To answer an incoming IM call by using UCWA:

1.  Handle the incoming **messagingInvitation** event sent from the **communication** resource. In the **messagingInvitation**-started event, cache the URI of the [accept](http://ucwa.skype.com/documentation/resources-accept) and [decline](http://ucwa.skype.com/documentation/resources-decline) resources.

2.  Decide to accept or reject the call invitation. You can prompt the user to choose an option provided by your application or use a different approach.

3.  To accept the invitation, submit a POST request on the **accept** resource. To reject the invitation, submit a POST request on the **decline** resource.

4.  Handle the incoming [message](http://ucwa.skype.com/documentation/resources-message) event notifications to receive incoming messages, and use the appropriate message decoder to parse the IM messages that it contains. To parse the messages, decode the URL-encoded blob by doing the following:
    
      - For HTML-formatted messages, follow the **htmlMessage** link to extract and parse the message.
    
      - For plain text messages, follow the **plainMessage** link to extract and parse the message.

## Get ready to answer a call

Before you answer an IM call, initialize your application. For more information, see [Get ready to make a call](making-an-outgoing-im-call-and-sending-messages.md).

To test the application, another caller must be online to make the call, using Lync, Skype, or a UCWA application.

## Answer the incoming call

To answer an incoming call, handle the incoming [messagingInvitation](http://ucwa.skype.com/documentation/resources-messaginginvitation) events sent from the [communication](http://ucwa.skype.com/documentation/resources-communication) resource. The following code example shows how to handle the **messagingInvitation** events.

``` csharp
        async void ProcessCommunicationEvents(IEnumerable<UcwaEvent> events)
        {
            foreach (var e in events)
            {
                switch (e.Name)
                {
                    case "messagingInvitation":
                        this.messagingInvite = new UcwaResourceMessageInvitation(e);
                        NotifyResourceStateChange(messagingInvite.State.ToLower(), messagingInvite.Name);

                        if (messagingInvite.Direction.ToLower() == "incoming")
                        {
                            // Cache the following URIs; otherwise, they might not be available on later messagingInvitation events.
                            if (messagingInvite.acceptUri != null) messagingInviteAcceptUri = messagingInvite.acceptUri;
                            if (messagingInvite.declineUri != null) messagingInviteDeclineUri = messagingInvite.declineUri;
                            if (messagingInvite.ThreadId != null) threadId = messagingInvite.ThreadId;
                            if (messagingInvite.ContainsResource("from"))
                            {
                                var from = new UcwaResourceParticipant(
                                    await messagingInvite.GetContainedResource("from", ucwaApp.Transport));
                                // Prompt the user to make the decision to Accept or Decline the call invitation.
                                NotifyMessagingInvite(this.messagingInvite.Subject, this.messagingInvite.Importance,
                                        from.DisplayName, this.messagingInvite.Message, this.messagingInvite.ThreadId);
                           }
                            else
                                ShowProcessProgress("WARN: messagingInvite does not specify valid 'from' resource");
                        }
                        break;
                    default:
                        break;
                }
            }
        }
```

The incoming **messageInvitation**-Started event will contain the links to the [accept](http://ucwa.skype.com/documentation/resources-accept) and [decline](http://ucwa.skype.com/documentation/resources-decline) resources. You will need to use them to accept or decline the call invitation. Cache these resources, because they will not be available in the subsequent **messagingInvitation** events, for example, when the invitation becomes Completed.

In the following code example, the application uses a [MessageDialog](http://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.popups.messagedialog.aspx) control for Windows Store apps to enable the user to accept or decline the call. This involves forwarding the invitation details, including the caller name, subject, and importance, to the UI thread and instantiating the **MessageDialog** in the application-defined OnMessagingInviteReceived event handler. The following code example shows the NotifyMessagingInvite method.

``` csharp
        async void NotifyMessagingInvite(string subject, string importance, string fromUri, string message, string threadId)
        {
            if (OnMessagingInviteReceived != null)
                await UcwaAppUtils.DispatchEventToUI(Windows.UI.Core.CoreDispatcherPriority.Normal,
                    new DispatchedHandler(() => { this.OnMessagingInviteReceived(subject, importance, fromUri, message, threadId); }));
        }
```

To see how to implement this method, download the [Lync 2013: UCWA Windows Store app to start and accept IM calls](http://code.msdn.microsoft.com/lync-2013-ucwa-windows-2f0ce645) sample application.

If the user accepts the call, the OnMessaginInviteRecieved event handler invokes the AcceptInvite() command. If the user declines the invitation, it invokes the DeclineInvite() command, as shown in the following example.

``` csharp
        async void Communication_OnMessagingInviteReceived(string subject, string importance, string fromUri, string firstMessage, string threadId)
        {
            await HandleMessagingInvite(subject, importance, fromUri, firstMessage, threadId);
        }

        List<string> handledMessagingInvites = new List<string>();
        public async Task HandleMessagingInvite(string subject, string importance, string fromUri, string firstMessage, string threadId)
        {
            if (handledMessagingInvites.Contains(threadId))
                return;

            handledMessagingInvites.Add(threadId);
            var msg = string.Format("Caller:\t{0}\r\nSubject:\t{1}\r\nImportance:\t{2}\r\nMessage:\t{3}\r\n", fromUri, subject, importance, firstMessage);
            var title = "You've got an incoming call!";
            // Display a popup window to inform the user of the incoming invitation.
            var msgDialog = new Windows.UI.Popups.MessageDialog(msg, title);

            msgDialog.Commands.Add(new UICommand("Accept", async (command) =>
            {
                var result = await this.ucwaApp.Communication.AcceptInvite();
                if (result.StatusCode == HttpStatusCode.OK || result.StatusCode == HttpStatusCode.NoContent)
                {
                    sendButton.IsEnabled = true;
                    textBlockStatus.Text += "Incoming call accepted. ";
                }
                else
                {
                    textBlockStatus.Text += "Error while accepting call. ";
                }
            }));
            msgDialog.Commands.Add(new UICommand("Decline", async (command) =>
            {
                var result = await this.ucwaApp.Communication.DeclineInvite();
                if (result.StatusCode == HttpStatusCode.OK || result.StatusCode == HttpStatusCode.NoContent)
                {
                    sendButton.IsEnabled = false;
                    textBlockStatus.Text += "Incoming call declined. ";
                }
                else
                {
                    textBlockStatus.Text += "Error while declining call. " + result.Exception.Message;
                }

            }));
            msgDialog.DefaultCommandIndex = 1;
            await msgDialog.ShowAsync();

        }
```

The AcceptInvite command submits a POST request on the **accept** resource that the cached messagingInviteAcceptUri variable points to.

``` csharp
        public async Task<UcwaAppOperationResult> AcceptInvite()
        {
            if (string.IsNullOrEmpty(messagingInviteAcceptUri))
                return new UcwaAppOperationResult(HttpStatusCode.NotFound, new Exception("Invalid messagingInvite Accept Uri"));
            return await this.ucwaApp.Transport.PostResourceAsync(messagingInviteAcceptUri, null as System.Net.Http.HttpContent);
        }
```

The DeclineInvite command submits a POST request on the **decline** resource that the cached messagingInviteDeclineUri variable points to.

``` csharp
        public async Task<UcwaAppOperationResult> DeclineInvite()
        {
            if (string.IsNullOrEmpty(messagingInviteDeclineUri))
                return new UcwaAppOperationResult(HttpStatusCode.NotFound, new Exception("Invalid messagingInvite Decline Uri"));
            return await this.ucwaApp.Transport.PostResourceAsync(messagingInviteDeclineUri, null as System.Net.Http.HttpContent);
        }
```

When the messaging invitation is accepted, the **messagingInvitation** state changes to connected and the call is established. You are then ready to receive incoming messages.

## Receive incoming IM messages

To receive an incoming IM message, handle incoming **message** events sent from the connected **conversation** resource. In addition to the actual message text, the event data includes other information about the message, including the participant who sent the message and the time stamp when the message is sent. You can extract and present this data in a user display, as shown in the following example.

``` csharp
        async void ProcessConversationEvents(IEnumerable<UcwaEvent> events)
        {
            foreach (var e in events)
            {
                switch (e.Name)
                {
                    case "message":
                        var msgRes = new UcwaResourceMessage(e);
                        if (msgRes.Direction.ToLower() == "incoming")
                        {
                            var status = msgRes.Status;
                            if (!participantNames.ContainsKey(msgRes.participantResourceUri))
                            {
                                var dn = await GetContactName(msgRes.contactResourceUri);
                                if (!string.IsNullOrEmpty(dn))
                                {
                                    participantNames.Add(msgRes.participantResourceUri, dn);
                                }
                            }
                            var participantName = participantNames[msgRes.participantResourceUri];
                            string timeStamp;
                            DateTime dateTimeStamp;
                            if (DateTime.TryParse(msgRes.TimeStamp, out dateTimeStamp))
                                timeStamp = dateTimeStamp.ToString();
                            else 
                                timeStamp="";
                            string msgText = ParseMessageText(msgRes); 
                            NotifyReceivedMessage(status, timeStamp, msgText, participantName);
                        }
                        break;
                    default:
                        break;
                }
            }
        }
```

The NotifyReceivedMessages forwards the data to the UI thread that displays the message in a conversation window. You'll need to parse the message text.

## Parse received IM messages

UCWA can support HTML and plain text messages. When Lync sends an IM message, the incoming message is a URL-encoded HTML tagged string, as shown in the following [message](http://ucwa.skype.com/documentation/resources-message) event example.

```xml
<resource rel="message" href="/ucwa/oauth/v1/applications/102270403677/communication/conversations/fcd168a1-fe9e-4604-a9b1-8acd4f013339/messaging/messages/2" xmlns="http://schemas.microsoft.com/rtc/2012/03/ucwa">
  <link rel="contact" href="/ucwa/oauth/v1/applications/102270403677/people/johndoe@contoso.com" />
  <link rel="participant" href="/ucwa/oauth/v1/applications/102270403677/communication/conversations/fcd168a1-fe9e-4604-a9b1-8acd4f013339/participants/johndoe@contoso.com" title="John Doe" />
  <link rel="messaging" href="/ucwa/oauth/v1/applications/102270403677/communication/conversations/fcd168a1-fe9e-4604-a9b1-8acd4f013339/messaging" />
  <link rel="htmlMessage" href="data:text/html;charset=utf-8,%3cspan+style%3d%22margin-bottom%3a0pt%3bfont-size%3a10pt%3bline-height%3anormal%3b%22%3eHello!%3c%2fspan%3e" />
  <property name="direction">Incoming</property>
  <property name="timeStamp">2014-06-02T21:00:13.1350704Z</property>
</resource>
```

This incoming message contains the HTML tagged text \<span style="margin-bottom:0pt;font-size:10pt;line-height:normal;"\>Hello\!\</span\>. This message is URL-encoded as %3cspan+style%3d%22margin-bottom%3a0pt%3bfont-size%3a10pt%3bline-height%3anormal%3b%22%3eHello\!%3c%2fspan%3e. The whole message is attached as the href attribute value of the htmlMessage link.

The plain text message is packaged as a URL-encoded string and attached as the href attribute value of the plainMessage link.

To parse the messages, you can use the [UrlDecode](http://msdn.microsoft.com/en-us/library/system.net.webutility.urldecode\(v=vs.110\).aspx) method on the [WebUtility](http://msdn.microsoft.com/en-us/library/system.net.webutility\(v=vs.110\).aspx) class of the [System.Net](http://msdn.microsoft.com/en-us/library/system.net\(v=vs.110\).aspx) namespace, as shown in the following example.

``` csharp
        string ParseMessageText(UcwaResourceMessage msgRes)
        {
            if (msgRes.HtmlMessage != null)
            {
                return Windows.Data.Html.HtmlUtilities.ConvertToText(
                   WebUtility.UrlDecode(msgRes.HtmlMessage));
            }
            else if (msgRes.PlainMessage != null)
            {
                return WebUtility.UrlDecode(msgRes.PlainMessage);
            }
        }
```

Here, [UrlDecode](http://msdn.microsoft.com/en-us/library/system.net.webutility.urldecode\(v=vs.110\).aspx) translates the URL-encoded string into an HTML string and [HtmlUtilities.ConvertToText](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.data.html.htmlutilities.converttotext.aspx) removes the HTML tags to extract the plain text value of the \<span\> element. For a plain text message, skip the call to [ConvertToText](http://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.data.html.htmlutilities.converttotext.aspx).

## See also

  - [Getting Started](http://ucwa.skype.com/documentation/getting-started) with UCWA 1.0

  - UCWA 1.0 [Event Channel Details](http://ucwa.skype.com/documentation/gettingstarted-events)

  - UCWA 1.0 [events](http://ucwa.skype.com/documentation/resources-events) resource reference page

  - [Set up the UCWA event channel to receive incoming notifications](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md)

  - [Set up the UCWA event channel to receive incoming notifications](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md)

  - [Making an outgoing IM call and sending messages](making-an-outgoing-im-call-and-sending-messages.md)

  - [Lync 2013: UCWA Windows Store app to start and accept IM calls](http://code.msdn.microsoft.com/lync-2013-ucwa-windows-2f0ce645) sample application

