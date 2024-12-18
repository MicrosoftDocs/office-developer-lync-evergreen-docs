---
title: 'Beyond the basics: Content sharing'
TOCTitle: Content sharing
ms:assetid: 18424c72-2863-48f3-81c9-6deaecc42c5b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937267(v=office.15)
ms:contentKeyID: 50877085
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Beyond the basics: Content sharing

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about using Microsoft Lync 2013 SDK to handle meeting content sharing events and shared content item presentation in Lync 2013 meetings.



**Applies to**: Lync 2013 | Lync Server 2013


<div class="caption">
Watch the video: Share file attachments in online meetings
</div>
<br />

> [!VIDEO a64fda42-3d5f-4ee9-90ef-2b8ab2e39024]

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

