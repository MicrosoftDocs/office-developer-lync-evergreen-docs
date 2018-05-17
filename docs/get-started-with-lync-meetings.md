---
title: Get started with Lync meetings
TOCTitle: Lync meetings
ms:assetid: 99fca176-e2b5-494a-8b2b-fa378d2b7a1e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933123(v=office.15)
ms:contentKeyID: 50877263
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Get started with Lync meetings

Learn about the programming concepts and Microsoft Lync 2013 SDK object model that you use to add Lync 2013 meeting lifecycle management features to an application.


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
What is Microsoft Lync 2013 meeting lifecycle management?  
Get started with Lync meetings  
What can you do with Lync meetings?  
Beyond the basics: Learn more about Lync meetings  
Additional resources  

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="get-started-with-lync-meetings.md" class="uri">get-started-with-lync-meetings.md</a>   <a href="get-started-with-lync-meetings.md" class="uri">get-started-with-lync-meetings.md</a>   <a href="get-started-with-lync-meetings.md" class="uri">get-started-with-lync-meetings.md</a></p></td>
</tr>
</tbody>
</table>


## What is Microsoft Lync 2013 meeting lifecycle management?

The classes in the [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md) and [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md) namespaces are the building blocks for features let you manage the lifecycle of an online Lync 2013 meeting. With these classes, you can start an online meeting, set the meeting access rule, invite participants, promote and demote participants, remove participants, control the content sharing stage of a meeting conversation window, and end meetings.

## Get started with Lync meetings

The prerequisites for working with Lync meetings are as follows:

  - Microsoft Lync 2013

  - Sign-in credentials for Microsoft Lync Server 2013

  - Microsoft Lync 2013 SDK

### Lync meeting essentials

To understand how to work with Lync meetings, it is important to become familiar with the concepts in the following table.

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
<td><p><a href="meeting-lobby-management.md">Meeting lobby management</a></p></td>
<td><p>Learn about meet-now meeting access types in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="shareable-meeting-content.md">Shareable meeting content</a></p></td>
<td><p>Learn about the nature of shareable content in a Microsoft Lync 2013 conversation and what content sharing feature that Microsoft Lync 2013 SDK lets you build into an application.</p></td>
</tr>
<tr class="odd">
<td><p><a href="content-sharing-modality.md">Content sharing modality</a></p></td>
<td><p>Learn about the Microsoft Lync 2013 conversation modality that is used to administer meeting content in an online meeting.</p></td>
</tr>
</tbody>
</table>


## What can you do with Lync meetings?

The following table lists basic tasks for working with Lync meetings.

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
<td><p><a href="how-to-start-a-meet-now-meeting.md">How to: Start a meet-now meeting</a></p></td>
<td><p>Learn how to start a Microsoft Lync 2013 meet-now meeting and register for meeting lobby events.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-set-meeting-access.md">How to: Set meeting access</a></p></td>
<td><p>Learn how to programmatically set the access type of a Microsoft Lync 2013 meet-now meeting.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-admit-or-deny-people-in-the-meeting-lobby.md">How to: Admit or deny people in the meeting lobby</a></p></td>
<td><p>Learn about programmatically admitting a user or denying user admission to a Microsoft Lync 2013 meet-now meeting from the meeting lobby.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-pin-and-lock-a-participant-video.md">How to: Pin and lock a participant video</a></p></td>
<td><p>Learn about programmatically locking and pinning meeting participant video feeds in a Microsoft Lync 2013 meet-now meeting.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-manage-meeting-presenters.md">How to: Manage meeting presenters</a></p></td>
<td><p>Learn how to programmatically promote participants to the presenter role in a Microsoft Lync 2013 meeting.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-share-a-whiteboard.md">How to: Share a whiteboard</a></p></td>
<td><p>Learn how to share a whiteboard collaboration session in a Microsoft Lync 2013 conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-share-a-powerpoint-slide-deck.md">How to: Share a PowerPoint slide deck</a></p></td>
<td><p>Learn how to programmatically share a PowerPoint slide deck session in a Microsoft Lync 2013 conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-attach-a-file-to-the-content-stage-of-a-conversation.md">How to: Attach a file to the content stage of a conversation</a></p></td>
<td><p>Learn how to attach a native file to a Microsoft Lync 2013 conversation and then download a file from a conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-get-a-shareable-resource-and-share-it-in-a-conversation.md">How to: Get a shareable resource and share it in a conversation</a></p></td>
<td><p>Learn how to use classes in Microsoft Lync 2013 SDK to select a locally shareable resource such as a desktop, monitor, or running program and then share it in a Microsoft Lync 2013 conversation.</p></td>
</tr>
</tbody>
</table>


## Beyond the basics: Learn more about Lync meetings

The following table lists advanced concepts for working with Lync meetings.

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
<td><p><a href="meeting-dial-in-access-keys.md">Meeting dial-in access keys</a></p></td>
<td><p>Learn about Microsoft Lync 2013 meeting access keys for dialing in to an online Lync 2013 meeting that is started from an application.</p></td>
</tr>
<tr class="even">
<td><p><a href="meeting-lobby-management.md">Meeting lobby management</a></p></td>
<td><p>Learn about meet-now meeting access types in Microsoft Lync 2013 SDK.</p></td>
</tr>
</tbody>
</table>


## Additional resources

  - [Get started with Lync 2013 SDK](get-started-with-lync-2013-sdk.md)

  - [Core concepts: Lync meetings](core-concepts-lync-meetings.md)

  - [What you can do with Lync meetings](what-you-can-do-with-lync-meetings.md)

  - [Beyond the basics: Lync meetings](beyond-the-basics-lync-meetings.md)

