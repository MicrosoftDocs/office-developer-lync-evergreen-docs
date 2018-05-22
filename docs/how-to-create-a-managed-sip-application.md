---
title: 'How to: Create a managed SIP application'
TOCTitle: 'How to: Create a managed SIP application'
ms:assetid: 8bb54a38-b568-48d0-9b62-7ad4c4770e37
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439082(v=office.15)
ms:contentKeyID: 57096239
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Create a managed SIP application

Learn how to create a managed SIP application in a Microsoft Lync Server 2013 deployment.


_**Applies to:** Lync Server 2013_

## Creating a managed SIP application for Lync Server

Creating a managed SIP application involves the following tasks:

  - Create and compile an application manifest.

  - Initialize a ServerAgent object.

  - Catch message dispatching events in an event loop.

  - Implement an event handler that processes the SIP messages that are dispatched from the Microsoft SIP Processing Language (MSPL) script that is embedded in the application manifest.

### Creating and compiling an application manifest

The first step in creating a managed Lync Server 2013 SIP application is to create an [application manifest](sip-application-manifest.md) and compile it within your application. The application manifest contains a message filter script that runs on the server and dispatches only the SIP messages that your application is interested in receiving. This action is usually performed in the **Main** method of the managed code application, as follows.

``` csharp
using System.Threading;
using System.Resources;
using Microsoft.Rtc.Sip;
...

// Obtain an XML string that contains your application manifest.
// In the sample below, the XML string is contained with the
// application assembly as a resource, and retrieved using the
// ResourceManager.GetString(resourceName) method.

ResourceManager myResourceManager = new ResourceManager(myApplicationClass);

// The "appManifest" string should be the name you gave your application
// manifest XML file when you added it as a resource to your application's
// assembly.

string myAppManifestXmlString = myResourceManager.GetString("appManifest");

ApplicationManifest myAppManifest = new ApplicationManifest(myAppManifestXmlString);

try {
myAppManifest.Compile();
}
catch (CompilerErrorException cee) {
Console.WriteLine("The following errors occurred during compilation:");
foreach (string errorMessage in cee.ErrorMessages) {
   Console.WriteLine("--- {0}", errorMessage);
}
}
```

### Initializing a ServerAgent object

The common point of communication between the Lync Server 2013 computer and your application is a [ServerAgent](https://msdn.microsoft.com/en-us/library/jj266157\(v=office.15\)) object. This object sends and receives messages through Lync Server 2013 on behalf of your application.

The [ServerAgent](https://msdn.microsoft.com/en-us/library/jj266157\(v=office.15\)) object must bind to the [ApplicationManifest](https://msdn.microsoft.com/en-us/library/jj265493\(v=office.15\)) object that is created in the previous section. As shown in the following example, this binding process is established when the **ServerAgent** is created.

``` csharp
try {
ServerAgent myAppServerAgent = new ServerAgent(myAppManifest);
}
catch (NullReferenceException nre) {
Console.WriteLine("The application manifest is uncompiled and ServerAgent cannot be instantiated.");
}
catch (ServerNotFoundException snfe) {
Console.WriteLine("The Lync Server computer is not available.");
}
```

The invocation of the previous ServerAgent constructor fails if the supplied application manifest does not compile with the MSPL compiler. In this case, a [NullReferenceException](http://msdn.microsoft.com/en-us/library/system.nullreferenceexception.aspx) is thrown. Therefore, your code should ensure that the application manifest compiles successfully before instantiating a **ServerAgent** instance.

Calling the previous constructor is applicable in a script-only application where the MSPL script is used to filter and process SIP messages and no messages are dispatched from the MSPL script to the managed code.

If the managed application handles messages that are dispatched from the MSPL message filter, the managed application must implement a message handler that is used to process the SIP messages that are dispatched from the MSPL message filter. For example, if the message filter calls the [Dispatch](https://msdn.microsoft.com/en-us/library/hh364714\(v=office.15\)) function as shown in the following example, the managed application must have a message handler named OnInviteReceived.

``` csharp
Dispatch("OnInviteReceived");
```

In addition, the class implementing this method must also bind to the newly created [ServerAgent](https://msdn.microsoft.com/en-us/library/jj266157\(v=office.15\)) object as shown in the next example.

``` csharp
ServerAgent myServerAgent = new ServerAgent(myClassWithDispatchMethods, myAppManifest);
```

### Catching message dispatching events in an event loop

When **Dispatch** is called from the MSPL script, a server event is raised. The managed application must catch this event to process the dispatched messages. To catch the event, the application can leverage the signaling capability of the [WaitHandle](https://msdn.microsoft.com/en-us/library/jj265810\(v=office.15\)) property that is exposed by the **ServerAgent** object in a loop. When the Lync Server instance receives a dispatched message, it raises a signal on the [WaitHandle](http://msdn.microsoft.com/en-us/library/9f7e54k1) object. The application can wait for the signal by calling [WaitOne](http://msdn.microsoft.com/en-us/library/58195swd) (or [WaitAny](http://msdn.microsoft.com/en-us/library/tdykks7z) if other application signals are being handled) on the **ServerAgent** object. If this method returns true (or a positive integer containing the index to the signaled callback in your handle array, in the case of **WaitAny**), the [ProcessEvent(Object)](https://msdn.microsoft.com/en-us/library/jj265491\(v=office.15\)) method must be called on the **ServerAgent** instance. The **ProcessEvent** passes the dispatched message to the event handler specified in the call to **Dispatch**.

Each application has its own process and is responsible for creating its own threads. The Microsoft Lync Server 2013 SIP Application Managed API does not require a specific threading model. However, the .NET Framework provides a **ThreadPool** class that can be used for this particular purpose. You can use **ThreadPool** to create a queue for events as shown in the following code example, which services a single input from the Lync Server 2013 computer.

``` csharp
ManualResetEvent autoResetEvent = new ManualResetEvent(false);
WaitHandle[] handleArray = new WaitHandle[] {
                              myAppServerAgent.WaitHandle,
                              manualResetEvent
                           };

WaitCallback waitCallback = new WaitCallback(myAppServerAgent.ProcessEvent);

while (true)
{
   int signaledEvent = WaitHandle.WaitAny(handleArray);

   if (signaledEvent == 0)  // The server event wait handle (index = 0) in handleArray was signaled
   {

       // Schedule a worker thread to process the server event.
       try
       {
          if (!ThreadPool.QueueUserWorkItem(waitCallBack))
          {
              Console.WriteLine("QueueUserWorkItem fails, quitting.");
              return;
          }

       }
       catch (Exception e)
       {
          Console.WriteLine("Unexpected exception: {0}\n{1}",
                            e.Message,
                            e.StackTrace);
       }
    }
    else // Manual reset event handle (index = 1) in handle array was signaled
    {
       Console.WriteLine("Quit handle signaled, worker will quit now\n");
       break;
    }
}
```


> [!NOTE]
> <P>The <STRONG>ServerAgent</STRONG> class includes the <STRONG>ServerAgent.ProcessEvent</STRONG> callback property that is used specifically for event signaling. Passing this callback to a <STRONG>WaitCallback</STRONG> delegate adds each Lync Server 2013 generated event (calls to <STRONG>Dispatch</STRONG> in the message filter) to a work queue that is obtained from the thread pool.</P>



### Implementing the message event handler

To receive messages from the Lync Server 2013 computer, your application manifest must dispatch them to the application. Within the application manifest, the MSPL built-in **Dispatch** function is used to send the current message to a supplied handler in your application, as shown in the following example.

    if (sipRequest.Method == "MESSAGE")
    Dispatch("OnMessageReceived");
    Respond(200);
    }

The previous script causes Lync Server 2013 to dispatch any message with a SIP method type of "MESSAGE" to the "OnMessageReceived" event handler in your application, passing the request as a [RequestReceivedEventArgs](https://msdn.microsoft.com/en-us/library/jj265762\(v=office.15\)) object. The following example shows how to define the handler.

``` csharp
public void OnMessageReceived(object sender, RequestReceivedEventArgs requestEventArgs) {

// Obtain the Request object to process from RequestReceivedEventArgs.
Request request = requestEventArgs.Request;

// Obtain the new server transaction for this request.
ServerTransaction myServerTransaction = requestEventArgs.ServerTransaction;

// Processing logic here.
// ...

// Create a branch on the server transaction to forward the request.
try
{
   // Attempt to send the request.
   requestEventArgs.ServerTransaction.CreateBranch();
   requestEventArgs.SendRequest(request);
}
catch (Exception e)
{
   Console.WriteLine("Unexpected exception: {0}\n{1}",
                            e.Message,
                            e.StackTrace);
}
}
```


> [!NOTE]
> <P>The method signature of your message handler must match that of the <A href="https://msdn.microsoft.com/en-us/library/jj266279(v=office.15)">RequestReceivedEventHandler</A> delegate, which takes an <STRONG>object</STRONG> as the first parameter, and a <STRONG>RequestReceivedEventArgs</STRONG> reference as the second parameter.</P>



To dispatch the methods, **ServerAgent**.ProcessEvent must be called if a server event is signaled with **ServerAgent.WaitHandle**. This method passes the dispatched message to the event handler that is registered with the corresponding MSPL **Dispatch** call.

## See also

#### Concepts

[Managed SIP Application API](managed-sip-application-api.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

