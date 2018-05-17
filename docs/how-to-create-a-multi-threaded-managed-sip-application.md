---
title: 'How to: Create a multi-threaded managed SIP application'
TOCTitle: 'How to: Create a multi-threaded managed SIP application'
ms:assetid: ba79c6fe-f761-43df-9bac-c5453981c3f0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439081(v=office.15)
ms:contentKeyID: 57096238
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Create a multi-threaded managed SIP application

Learn how to create a multi-threaded SIP application in a Microsoft Lync Server 2013 deployment.


_**Applies to:** Lync Server 2013_

## Creating a multi-threaded SIP application

For performance and efficiency, Lync Server 2013 events can be handled with worker threads from the .NET Framework thread pool.

A simple approach is to use the .NET Framework thread pool and queue each event from the server (for example, use a call from [Dispatch](https://msdn.microsoft.com/en-us/library/hh364714\(v=office.15\))) as a user work item. In the next code sample, the server signals an event with the [WaitHandle](https://msdn.microsoft.com/en-us/library/jj265810\(v=office.15\)) property that is provided by the [ServerAgent](https://msdn.microsoft.com/en-us/library/jj266157\(v=office.15\)) instance. After the event is signaled, the application attempts to create a worker thread from the thread pool, which is then used to service the event. The [ProcessEvent(Object)](https://msdn.microsoft.com/en-us/library/jj265491\(v=office.15\)) event callback method is passed to the thread, which removes the event (the dispatch) from the server queue and processes it by passing the SIP message to the method that is specified in the Microsoft SIP Processing Language (MSPL) call to **Dispatch**.

The next code sample demonstrates the basic structure that is used for threading dispatches from the server. It can be called directly from the **Main()** (entry point) method of your application, taking an instance of **ServerAgent** as a parameter.

``` csharp
public void LCServerEventHandler(ServerAgent sa)
{
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

          // Schedule a worker thread to process the server event
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
}
```

## See also

#### Concepts

[Managed SIP Application API](managed-sip-application-api.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

