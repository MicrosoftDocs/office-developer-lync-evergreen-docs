---
title: Retrieve chat rooms by using user membership (SampleRiamo)
TOCTitle: Retrieve chat rooms by using user membership (SampleRiamo)
ms:assetid: e89be182-e681-4205-8229-802c72fc50d5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465908(v=office.15)
ms:contentKeyID: 57101414
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Retrieve chat rooms by using user membership (SampleRiamo)

Learn about the Microsoft Lync Server 2013 Persistent Chat SDK SampleRiamo application.


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
To set up the project in Visual Studio 2010  
To add the source code to the project  
Requirements  


> [!NOTE]
> <P>By default, the SampleRiamo application is copied to the %ProgramFile%\Microsoft Lync Server 2013\Persistent Chat SDK\SampleRiamo folder. SampleRiamo and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-1a96c974">MSDN Code Gallery</A>.</P>



This sample application shows how to retrieve a list of chat rooms of which the user is a member and the user can manage. For an example of how to use an existing chat room, see [Create and join a chat room and participate in chat (SampleChat)](create-and-join-a-chat-room-and-participate-in-chat-samplechat.md) or [Maintain load-balance on the server (SampleLoadTest)](maintain-load-balance-on-the-server-sampleloadtest.md).

## To set up the project in Visual Studio 2010

1.  On the Microsoft Visual Studio 2010 **File** menu, point to **New**, and then choose **Project**.

2.  In the **Project types** pane, choose **Visual C\#**, and then choose **Windows**.

3.  In the **Templates** pane, choose **Console Application**.

4.  In the **Name** box, type the name of the project, and then click **OK**. Visual Studio creates a new project.

5.  In the Solution Explorer, right-click **Properties** under the newly created project, and then click **Open**.

6.  In the newly opened **Properties** tab in Visual Studio main window, set **Platform target** to either x64 or AnyCPU under the **Build** option, and then set **Target framework** to .NET Framework 4 under the **Application** option.

7.  In the Solution Explorer, right-click **References** under the newly created project, and then select **Add Reference**.

8.  Select the **Browse** tab, navigate to the Lync Server 2013 Persistent Chat SDK installation directory, and then select the **Microsoft.Rtc.Collaboration.DLL** and **Microsoft.Rtc.Collaboration.PersistentChat.DLL** assembly files.

## To add the source code to the project

1.  Replace Program.cs with the SampleRiamo.cs.

2.  Add SampleCommon.cs to the project.

3.  Press **F5** to run the application in Debug mode.

## Requirements

  - Microsoft Visual Studio 2010 or Visual Studio 2012 development system

  - .NET Framework 4.5 (installed automatically with Visual Studio 2012 or separately with Visual Studio 2010)

  - UcmaRedist.msi

  - UcgcRedist.msi

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

