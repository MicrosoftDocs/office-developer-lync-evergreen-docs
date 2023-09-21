---
title: Get started with desktop, application, and display sharing
TOCTitle: Desktop, application, and display sharing
ms:assetid: fd565e29-da05-4cb5-9fd5-a786d3790e4e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933246(v=office.15)
ms:contentKeyID: 50877392
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Get started with desktop, application, and display sharing

Learn the programming concepts and Microsoft Lync 2013 SDK object model for building an application that manages desktop, application, and display sharing in a Microsoft Lync 2013 conversation.



**Applies to**: Lync 2013 | Lync Server 2013

 

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="get-started-with-desktop-application-and-display-sharing.md#Start" class="uri"><img src="images/JJ933215.mod_icon_getstartbox(Office.15).gif"/></a>   <a href="get-started-with-desktop-application-and-display-sharing.md#Do" class="uri"><img src="images/JJ933215.mod_icon_dobox(Office.15).gif"/></a>   <a href="get-started-with-desktop-application-and-display-sharing.md#Learn" class="uri"><img src="images/JJ933215.mod_icon_startbox(Office.15).gif"/></a></p></td>
</tr>
</tbody>
</table>

## What are desktop, application, and display sharing?

Microsoft Lync 2013 provides a modality that allows a Lync conversation participant to share a resource such as a view of a Windows desktop, a running application, or a monitor with other conversation participants. The shared resource can be remotely controlled if the sharing participant allows it.

The shared resource is displayed in a component of the Lync conversation window that is known as the sharing stage. It's not possible to share a computer resource through the Lync 2013 API without the use of the conversation window. For this reason, you cannot create a sharing application for use in a UI suppression scenario.
<a name="Start"></a> 

## Get started with desktop, application, and display sharing

The prerequisites for working with resource sharing are as follows:

  - Microsoft Lync 2013

  - Sign-in credentials for Microsoft Lync Server 2013

  - Microsoft Lync 2013 SDK

### Desktop, application, and display sharing essentials

To understand how to work with resource sharing, it's important to become familiar with the concepts in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concept</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="sharing-resources-in-a-conversation.md">Sharing resources in a conversation</a></p></td>
<td><p>Learn about programmatically sharing a computer monitor, desktop, or running program with another Microsoft Lync 2013 user in a conversation window by using classes in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="application-sharing-modality.md">Application sharing modality</a></p></td>
<td><p>Learn about the Lync SDK <strong>ApplicationSharingModality</strong> class and how it enables you to share resources in an application.</p></td>
</tr>
</tbody>
</table>
<a name="Do"></a> 

## What can you do with desktop, application, and display sharing?

The following table lists basic tasks for working with desktop, application, and display sharing.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Task</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="how-to-start-a-resource-sharing-conversation.md">How to: Start a resource sharing conversation</a></p></td>
<td><p>Learn how to start a Microsoft Lync 2013 sharing conversation and get a list of shareable resources that are shared in the conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-get-a-shareable-resource-and-share-it-in-a-conversation.md">How to: Get a shareable resource and share it in a conversation</a></p></td>
<td><p>Learn how to use classes in Microsoft Lync 2013 SDK to select a locally shareable resource such as a desktop, monitor, or running program and then share it in a Microsoft Lync 2013 conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-accept-or-decline-a-request-to-control-a-shared-resource.md">How to: Accept or decline a request to control a shared resource</a></p></td>
<td><p>Learn how to accept or decline a request to control a locally shared resource in a Microsoft Lync 2013 conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-grant-and-revoke-control-of-a-shared-resource.md">How to: Grant and revoke control of a shared resource</a></p></td>
<td><p>Learn how to grant and revoke control of a locally shared resource in a Microsoft Lync 2013 conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-request-and-release-control-of-a-shared-resource.md">How to: Request and release control of a shared resource</a></p></td>
<td><p>Learn how to request control of a computer resource that is shared by another Microsoft Lync 2013 conversation participant.</p></td>
</tr>
</tbody>
</table>
<a name="Learn"></a> 

## Beyond the basics: Learn more about desktop, application, and display sharing

The following table lists advanced concepts for working with desktop, application, and display sharing.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concept</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="application-sharing-modality-event-handling.md">Application sharing modality event handling</a></p></td>
<td><p>Learn about making your application UI responsive to the events raised by Microsoft Lync 2013 API application sharing modality in Microsoft Lync 2013 conversations.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Get started with Lync 2013 SDK](get-started-with-lync-2013-sdk.md)

  - [Core concepts: Desktop, application, and display sharing in Lync SDK](core-concepts-desktop-application-and-display-sharing-in-lync-sdk.md)

  - [What you can do with desktop, application, and display sharing](what-you-can-do-with-desktop-application-and-display-sharing.md)

  - [Beyond the basics: Desktop, application, and display sharing](beyond-the-basics-desktop-application-and-display-sharing.md)

