---
title: Lync Controls architecture
TOCTitle: Lync Controls architecture
ms:assetid: 2d7c1fac-8ec0-4e83-b494-5b09af844c90
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937293(v=office.15)
ms:contentKeyID: 50877118
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Lync Controls architecture

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the basic process architecture of the Microsoft Lync 2013 Controls and their relation to the Microsoft Lync 2013 client application.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Architecture overview<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Architecture overview

Each Microsoft Lync Controls application connects to Lync Server 2013 using a single out-of-process connection to Microsoft Lync 2013. The application is either a Microsoft Windows Presentation Foundation (WPF) or Microsoft Silverlight application containing Lync Controls. The application’s connection to Lync 2013 is created by the first Lync Control instantiated by the application. This first control configures the layer between Lync 2013 and the application. Figure 1 illustrates the relationship between a Lync 2013 Controls-based application and the Lync 2013 SIP endpoint of the Lync Server 2013.

The first instantiated Lync Control automatically performs the following tasks:

  - Adds Lync 2013 connectivity to a WPF or Silverlight application without requiring code-behind.

  - Allows use of multiple interfaces between Lync Controls and Lync 2013 in a single application.

  - Handles and exposes runtime errors.

  - Ensures shutdown of the layer between the Lync Controls application and Lync 2013.

Figure 1. Lync controls architecture

  
![Shows SL and WPF pages + Lync controls use server](images/JJ937293.LyncClientSDK_ControlsArchitecture(Office.15).png "Shows SL and WPF pages + Lync controls use server")

Each subsequent Lync Control opened by the application uses the existing connection. Because all Lync Controlscan perform initial tasks, you can focus on putting only the controls that implement the Lync features that you need on a window. In addition, you do not write any client-side initialization code.

To get the connection state, check the following properties:

  - [IsSignedIn](https://msdn.microsoft.com/library/hh346560\(v=office.15\)) property

  - [InitializationError](https://msdn.microsoft.com/library/hh379166\(v=office.15\)) property

  - [IsInResiliencyMode](https://msdn.microsoft.com/library/hh363627\(v=office.15\)) property

  - [InitializationErrorMessage](https://msdn.microsoft.com/library/hh379615\(v=office.15\)) property

For more information about checking connection state, see [Troubleshooting Lync Controls applications](troubleshooting-lync-controls-applications.md).

## See also

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [Lync Controls reference](lync-controls-reference.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

