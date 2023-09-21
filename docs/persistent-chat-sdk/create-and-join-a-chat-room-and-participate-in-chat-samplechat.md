---
title: Create and join a chat room and participate in chat (SampleChat)
TOCTitle: Create and join a chat room and participate in chat (SampleChat)
ms:assetid: 19dd9501-1642-4609-b3e6-385718d09632
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465906(v=office.15)
ms:contentKeyID: 57101412
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Create and join a chat room and participate in chat (SampleChat)

Learn about the Microsoft Lync Server 2013 Persistent Chat SDK SampleChat application.


**Applies to:** Lync 2013 | Lync Server 2013




> [!NOTE]
> <P>By default, the SampleChat application is copied to the %ProgramFile%\Microsoft Lync Server 2013\Persistent Chat SDK\SampleChat folder. SampleChat and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-9128722a">MSDN Code Gallery</A>.</P>



This sample application shows how to use the Microsoft Lync Server 2013 Persistent Chat API to complete the following tasks:

  - Connect to a Lync Server 2013 Persistent Chat on a [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\))-based [PersistentChatEndpoint](https://msdn.microsoft.com/library/jj267567\(v=office.15\)).

  - Create and join a chat room.

  - Participate chat in the chat room.

  - Get the chat history from the chat room.

  - Search the chat history of a chat room.

  - Leave the chat room.

  - Disconnect from the Lync Server 2013 Persistent Chat and the underlying Lync Server 2013.

## To set up the project in Visual Studio 2010

1.  On the Microsoft Visual Studio 2010 **File** menu, point to **New**, and then choose **Project**.

2.  In the **Project types** pane, choose **Visual C\#**, and then choose **Windows**.

3.  In the **Templates** pane, choose **Console Application**.

4.  In the **Name** box, enter the name of the project, and then click **OK**. Visual Studio creates a new project.

5.  In the Solution Explorer, right-click **Properties** under the newly created project, and then click **Open**.

6.  In the newly opened **Properties** tab in Visual Studio main window, set **Platform target** to either x64 or AnyCPU under the **Build** option, and then set **Target framework** to .NET Framework 4 under the **Application** option.

7.  In the Solution Explorer, right-click **References** under the newly created project, and then select **Add Reference**.

8.  Select the **Browse** tab, navigate to the Microsoft Lync Server 2013 Persistent Chat SDK installation directory, and then select the **Microsoft.Rtc.Collaboration.DLL** and **Microsoft.Rtc.Collaboration.PersistentChat.DLL** assembly files.

## To add the source code to the project

1.  Replace Program.cs with the SampleChat.cs.

2.  Add SampleCommon.cs to the project.

3.  Press **F5** to run the application in Debug mode.

## Requirements

  - Microsoft Visual Studio 2010 or Microsoft Visual Studio 2012 development system

  - .NET Framework 4.5. (installed automatically with Visual Studio 2012 or separately with Visual Studio 2010)

  - UcmaRedist.msi

  - UcgcRedist.msi

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

