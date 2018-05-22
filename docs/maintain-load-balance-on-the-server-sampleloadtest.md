---
title: Maintain load-balance on the server (SampleLoadTest)
TOCTitle: Maintain load-balance on the server (SampleLoadTest)
ms:assetid: 18ee5912-7407-4129-b6fc-22739384df28
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465918(v=office.15)
ms:contentKeyID: 57101467
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Maintain load-balance on the server (SampleLoadTest)

Learn about the Microsoft Lync Server 2013 Persistent Chat SDK SampleLoadTest application.


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
To set up the project in Visual Studio 2010  
To add the source code to the project  
Requirements  


> [!NOTE]
> <P>By default, the SampleLoadTest application is copied to the %ProgramFile%\Microsoft Lync Server 2013\Persistent Chat SDK\SampleLoadTest folder. SampleLoadTest and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-maintain-6b7eb57a">MSDN Code Gallery</A>.</P>



This sample application simulates a multiple-user load on Microsoft Lync Server 2013 Persistent Chat. It assumes that all users are created and SIP-enabled. The necessary category and chat rooms are created if they do not already exist on Lync Server 2013 Persistent Chat.

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

1.  Replace Program.cs with the SampleLoadTest.cs.

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

