---
title: Chat room features in Lync SDK
TOCTitle: Chat room features
ms:assetid: 332dedd9-d1bd-4f3b-9f40-56b271f1ddab
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937295(v=office.15)
ms:contentKeyID: 50877115
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Chat room features in Lync SDK

![What's new topic](images/JJ937254.mod_icon_whatsnew_long(Office.15).png "What's new topic")

Microsoft Lync 2013 SDK includes new Persistent Chat classes and shows how to use the new classes to add features to an application.

**Last modified:** April 05, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Persistent Chat features<br />
Additional resources</p></td>
<td><div class="caption">
Watch the video: What’s new with the Lync 2013 Persistent Chat API
</div>
<br />
&gt; [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/2e129dbc-529c-4e43-a7aa-70ce9249b338]</td>
</tr>
</tbody>
</table>

## Persistent Chat features

The following table describes the new Persistent Chat features in Microsoft Lync 2013 SDK.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Feature</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Chat room add-in</p></td>
<td><p>The add-in application feature lets you create a Silverlight add-in application that is hosted in a Lync 2013 host chat room. The hosting chat room starts one associated add-in in a window extension when a user opens the chat room window. The Lync 2013 API gives the hosted add-in access to the room and all message history in the room. This includes message text entered by the local user before it is posted to the room. This pending message text can be intercepted and altered or canceled.<br />
<br />
Use the message-related API to format and filter message text before it is posted to a room. In addition, an add-in can programmatically generate room messages to be posted to the hosting room on behalf of the local user. If a middle-tier bot has joined the room, an add-in can listen for messages from the bot and then reformat the messages as human-friendly text and display the message directly in the add-in. For information about creating an add-in, see <a href="get-started-with-persistent-chat.md">Get started with Persistent Chat</a>.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>Custom chat room</p></td>
<td><p>When Lync 2013 is running in UI suppression mode, you can still provide a chat room feature to a signed-in user. The API allows you to create a full chat room experience including a room participation list, access to all messages posted to a room, and message posting.<br />
<br />
Advanced features include access to a user’s followed room list, the ability to search for a room given a full or partial room name, and the ability to join a room or leave a room. For information about how to create a custom chat room, see <a href="what-you-can-do-with-persistent-chat.md">What you can do with Persistent Chat</a>.</p>
<p></p></td>
</tr>
</tbody>
</table>

## Additional resources

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

  - [Get started with Persistent Chat](get-started-with-persistent-chat.md)

