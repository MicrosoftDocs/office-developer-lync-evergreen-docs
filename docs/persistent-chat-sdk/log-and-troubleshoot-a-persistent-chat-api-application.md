---
title: Log and troubleshoot a Persistent Chat API application
TOCTitle: Log and troubleshoot a Persistent Chat API application
ms:assetid: 7fdb2465-f114-43b7-97ee-bc10ac93e260
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439207(v=office.15)
ms:contentKeyID: 57101350
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Log and troubleshoot a Persistent Chat API application

Learn how to create logs for and troubleshoot Microsoft Lync Server 2013 Persistent Chat SDK applications.


**Applies to:** Lync 2013 | Lync Server 2013

The Microsoft Lync Server 2013 Persistent Chat API includes built-in logging capabilities that can be enabled by a Lync Server 2013 Persistent Chat API application to trace the execution of the application. The logging is based on the [WPP Software Tracing](http://msdn.microsoft.com/library/ff556204\(v=vs.85\).aspx). The Microsoft Lync Server 2013 Logging Tool is provided to configure, start, stop, and analyze logs that are provided by the Persistent Chat library (Microsoft.Rtc.Collaboration.PersistentChat.DLL assembly) and other trace providers, also known as components. In addition, the Logging Tool includes a traffic view of SIP messages that are transported between the application and Lync Server 2013, including the server that is running Microsoft Lync Server 2013 Persistent Chat. The information can be useful for troubleshooting a Lync Server 2013 Persistent Chat API application.


> [!NOTE]
> <P>The Group Chat API file-based logging mechanism is no longer supported in the Lync Server 2013 Persistent Chat API.</P>



The Lync Server 2013 Logging Tool, OcsLogger.exe, it is included in the Microsoft Unified Communications Managed API 4.0 SDK and is located in the %programfiles%\\Microsoft UCMA 4.0\\Core\\Tracing folder.

### To log traces and messages in a Lync Server 2013 Persistent Chat API application by using the Logging Tool

1.  Start OcsLogger.exe

2.  Below **Logging Options** in the **Components** list, ensure that Collaboration, ChatSDK, ChatEndpoint and S4 are selected.

3.  Click the **Start Logging** button.

4.  Run the application or a part of the application.

5.  Click the **Stop Logging** button.

6.  Click the **Analyze Log Files** button, and then use the Snooper tool to examine the logged traces and captured SIP messages.


> [!NOTE]
> <P>The Lync Server 2013 Logging Tool and the log viewer, Snooper.exe, are distributed as part of the Microsoft Lync Server 2013 Debug Tools package, which is available for the on-premise customers at http://www.microsoft.com/download/.</P>



## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

#### Other resources

[Lync Server 2013 Logging Tool](http://technet.microsoft.com/library/gg558599.aspx)

