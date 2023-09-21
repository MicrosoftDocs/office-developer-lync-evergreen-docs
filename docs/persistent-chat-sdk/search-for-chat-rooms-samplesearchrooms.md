---
title: Search for chat rooms (SampleSearchRooms)
TOCTitle: Search for chat rooms (SampleSearchRooms)
ms:assetid: 3eaa91b7-b4e5-493d-8e2a-9d42bda43bae
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465917(v=office.15)
ms:contentKeyID: 57101470
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Search for chat rooms (SampleSearchRooms)

Learn about the Microsoft Lync Server 2013 Persistent Chat SDK SampleSearchRooms application.


**Applies to:** Lync 2013 | Lync Server 2013




> [!NOTE]
> <P>By default, the SampleSearchRooms application is copied to the %ProgramFile%\Microsoft Lync Server 2013\Persistent Chat SDK\SampleSearchRooms folder. SampleSearchRooms and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-37149baa">MSDN Code Gallery</A>.</P>



This sample application publishes your user colors and subscribes to the user colors of another user. This sample application demonstrates how to search for chat rooms using the Microsoft Lync Server 2013 Persistent Chat API.

## To set up the project in Visual Studio 2010

1.  On the Microsoft Visual Studio 2010 **File** menu, point to **New**, and then choose **Project**.

2.  In the **Project types** pane, choose **Visual C\#**, and then choose **Windows**.

3.  In the **Templates** pane, choose **Console Application**.

4.  In the **Name** box, type the name of the project, and then click **OK**. Visual Studio creates a new project.

5.  In the Solution Explorer, right-click **Properties** under the newly created project, and then click **Open**.

6.  In the newly opened **Properties** tab in Visual Studio main window, set **Platform target** to either x64 or AnyCPU under the **Build** option, and then set **Target framework** to .NET Framework 4 under the **Application** option.

7.  In the Solution Explorer, right-click **References** under the newly created project, and then select **Add Reference**.

8.  Select the **Browse** tab, navigate to the Lync Server 2013 Persistent Chat SDK installation directory, and then the select **Microsoft.Rtc.Collaboration.DLL** and **Microsoft.Rtc.Collaboration.PersistentChat.DLL** assembly files.

## To add the source code to the project

1.  Replace Program.cs with the SampleSearchRooms.cs.

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

