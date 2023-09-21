---
title: Get started with content sharing
TOCTitle: Content sharing
ms:assetid: 6316a1ec-f4b3-4a4e-93c2-9bc9eee84c9c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933066(v=office.15)
ms:contentKeyID: 50877196
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Get started with content sharing

Learn about the programming concepts and Microsoft Lync 2013 SDK object model for building an application that controls the content sharing stage in a Microsoft Lync 2013 conversation window.



**Applies to**: Lync 2013 | Lync Server 2013
 

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="get-started-with-content-sharing.md#Start" class="uri"><img src="images/JJ933215.mod_icon_getstartbox(Office.15).gif"/></a>   <a href="get-started-with-content-sharing.md#Do" class="uri"><img src="images/JJ933215.mod_icon_dobox(Office.15).gif"/></a>   <a href="get-started-with-content-sharing.md#Learn" class="uri"><img src="images/JJ933215.mod_icon_startbox(Office.15).gif"/></a></p></td>
</tr>
</tbody>
</table>

<div class="caption">
Watch the video: Share file attachments in online meetings
</div>
<br />

> [!VIDEO https://www.microsoft.com/videoplayer/embed/511512f2-745d-4b09-8849-db7c997743f4]


## What is content sharing?

Content sharing in a conversation or meeting involves making a common whiteboard available for all conversation participants to annotate or control. PowerPoint slide decks can also be shared on the common content sharing stage of a Lync 2013 conversation window. To enable offline collaboration, native files such as Word documents, Excel spreadsheets, or text files can be uploaded to and downloaded from the conversation content sharing stage.

<a name="Start"></a> 

## Get started with content sharing

After reviewing the topics in the following sections, you'll have enough information to implement the following content sharing features in your application:

  - Upload whiteboards and save annotations at the conclusion of a conversation.

  - Upload PowerPoint slide decks, scroll through slides, and then download slide decks presented by other users in the conversation.

  - Upload native files to the conversation sharing stage as attachments and then download the attachments.

### Content sharing essentials

To understand how to work with content sharing, it's important to become familiar with the concepts in the following table.

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
<td><p><a href="shareable-meeting-content.md">Shareable meeting content</a></p></td>
<td><p>Learn about the nature of shareable content in a Microsoft Lync 2013 conversation and what content sharing features that Microsoft Lync 2013 SDK lets you build into your application.</p></td>
</tr>
<tr class="even">
<td><p><a href="content-sharing-modality.md">Content sharing modality</a></p></td>
<td><p>Learn about the Microsoft Lync 2013 conversation modality that is used to administer meeting content in an online meeting.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

<a name="Do"></a>

## What can you do with content sharing?

The following table lists basic tasks for working with content sharing.

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
<td><p><a href="how-to-start-a-content-sharing-conversation.md">How to: Start a content sharing conversation</a></p></td>
<td><p>Learn how to start a Microsoft Lync 2013 conversation that hosts content sharing.</p></td>
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
<td><p><a href="how-to-save-and-clear-whiteboard-annotations.md">How to: Save and clear whiteboard annotations</a></p></td>
<td><p>Learn how to save and clear annotations made to a whiteboard in a Microsoft Lync 2013 conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-attach-a-file-to-the-content-stage-of-a-conversation.md">How to: Attach a file to the content stage of a conversation</a></p></td>
<td><p>Learn how to attach a native file to a Microsoft Lync 2013 conversation and then download a file from a conversation.</p></td>
</tr>
</tbody>
</table>

<a name="Learn"></a>

## Beyond the basics: Learn more about content sharing

The following table lists advanced concepts for working with content sharing.

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
<td><p><a href="content-sharing-modality-event-handling.md">Content sharing modality event handling</a></p></td>
<td><p>Learn about making your application UI responsive to the events raised by Microsoft Lync 2013 API content sharing modality in Microsoft Lync 2013 conversations.</p></td>
</tr>
<tr class="even">
<td><p><a href="shareable-content-event-handling.md">Shareable content event handling</a></p></td>
<td><p>Learn about making your Lync SDK-enabled application UI more responsive by handling events raised on the <a href="https://msdn.microsoft.com/library/jj277217(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ShareableContent</a> class.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Get started with Lync 2013 SDK](get-started-with-lync-2013-sdk.md)

  - [Core concepts: Content sharing in Lync SDK](core-concepts-content-sharing-in-lync-sdk.md)

  - [What you can do with content sharing](what-you-can-do-with-content-sharing.md)

  - [Beyond the basics: Content sharing](beyond-the-basics-content-sharing.md)

