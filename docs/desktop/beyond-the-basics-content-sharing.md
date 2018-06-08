---
title: 'Beyond the basics: Content sharing'
TOCTitle: Content sharing
ms:assetid: 18424c72-2863-48f3-81c9-6deaecc42c5b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937267(v=office.15)
ms:contentKeyID: 50877085
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Beyond the basics: Content sharing

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about using Microsoft Lync 2013 SDK to handle meeting content sharing events and shared content item presentation in Lync 2013 meetings.

**Last modified:** February 19, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Advanced content sharing programming<br />
In this section<br />
Additional resources</p></td>
<td><div class="caption">
Watch the video: Share file attachments in online meetings
</div>
<br />
&gt; [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/511512f2-745d-4b09-8849-db7c997743f4]</td>
</tr>
</tbody>
</table>

## Advanced content sharing programming

Your application must react to changes in the state of the content sharing modality and active shared content item to make your application UI responsive. For example, the UI of your application should have buttons to let a user take such actions as:

  - Add or remove an item from the meeting content bin.

  - Move an item to the sharing stage.

  - Clear or save annotations.

  - Take over as content presenter.

  - Download a meeting attachment.

These content-related actions can be unavailable, depending on the state of the content. As that state changes and the actions become available, your UI must be updated to give a user a hint that the actions can be performed.

As shareable content items are uploaded to a conversation or removed from a conversation, your UI should be updated to reflect the current collection of sharable content items. The content sharing modality for the conversation provides events that let you react to these changes.

## In this section

  - [Content sharing modality event handling](content-sharing-modality-event-handling.md)

  - [Shareable content event handling](shareable-content-event-handling.md)

## See also

  - [Beyond the basics in Lync 2013 SDK](beyond-the-basics-in-lync-2013-sdk.md)

  - [Core concepts: Content sharing in Lync SDK](core-concepts-content-sharing-in-lync-sdk.md)

  - [What you can do with content sharing](what-you-can-do-with-content-sharing.md)

