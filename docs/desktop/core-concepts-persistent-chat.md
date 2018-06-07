---
title: 'Core concepts: Persistent Chat'
TOCTitle: Persistent Chat
ms:assetid: cfa8efab-8ac7-4c43-ae72-d1234a73b7df
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933198(v=office.15)
ms:contentKeyID: 50877341
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Core concepts: Persistent Chat

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the foundational Microsoft Lync 2013 SDK objects that make up the programmable components of a Microsoft Lync 2013 Persistent Chat room.

**Last modified:** April 16, 2013

***Applies to:** Lync 2013 | Lync Server 2013*


Watch the video: What’s new with the Lync 2013 Persistent Chat API

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/2e129dbc-529c-4e43-a7aa-70ce9249b338]


## Persistent Chat overview

Microsoft Lync 2013 implements a set of Persistent Chat features that replace the Group Chat client, which is part of Microsoft Lync Server 2010. Microsoft Lync 2013 SDK gives you programmatic access to those features through its API.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Note" alt="Note" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>There are two kinds of chat rooms. A regular chat room accepts messages posted by any member of the chat room. The auditorium chat room lets a presenter post messages to the room and other room participants can only read those messages.</p></td>
</tr>
</tbody>
</table>

## Persistent Chat API features

The following Persistent Chat features can be enabled by using the Lync SDK Persistent Chat extensions.

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
<td><p>A chat room add-in is a Silverlight browser extension that is hosted in the Persistent Chat window in an extension pane. Developers use this chat room extension to add powerful custom features to the chat room experience. With an add-in, you can display relevant information from any source that you can access by using add-in logic. Source examples include room message history, Web services such as Bing, or internal company databases.<br />
<br />
The chat room add-in is also used to format chat room messages sent by a bot into a human-readable format and displayed in the add-in message area. The add-in can be used to reply to chat room messages, add client message filtering for outgoing messages, or format messages as they are sent to the chat room.<br />
<br />
For information about the capabilities of an add-in, see <a href="chat-room-add-in-application-in-lync-sdk.md">Chat room add-in application in Lync SDK</a>.</p>
<p></p>
<p></p></td>
</tr>
<tr class="even">
<td><p>Followed room list</p></td>
<td><p>Just like <a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Microsoft.Lync.Model.Contact</a> represents a contact in the contact list and <a href="https://msdn.microsoft.com/en-us/library/jj277245(v=office.15)">Microsoft.Lync.Model.Group.CustomGroup</a> represent custom groups in the contact list, <a href="https://msdn.microsoft.com/en-us/library/jj266467(v=office.15)">Microsoft.Lync.Model.Room.Room</a> represents a chat room in a contact list. A user automatically joins all chat rooms in the contact list when they sign in to Lync 2013. When joined to a chat room, room message alerts can be displayed according to the user’s preferences.</p></td>
</tr>
<tr class="odd">
<td><p>Chat room message posting</p></td>
<td><p>By using the chat room entry API extensions, a user can post messages to any chat room that has granted the user permission to post messages. If the room is an auditorium, the user must also be a presenter.</p></td>
</tr>
<tr class="even">
<td><p>Chat room search</p></td>
<td><p>The chat room search feature lets you create a room search UI that searches through all chat rooms provisioned on a server running Microsoft Lync Server 2013 Persistent Chat and join any chat room whose membership includes the user.</p></td>
</tr>
<tr class="odd">
<td><p>Persistent Chat message notifications</p></td>
<td><p>Persistent Chat message alerts are sent to a signed-in user for any Persistent Chat rooms that are being followed on the user’s client application. You can duplicate the Lync 2013 message alert experience in your client application by listening to message events on any joined room and notifying a user in any way that you choose.</p></td>
</tr>
</tbody>
</table>

## In this section

  - [Chat room add-in application in Lync SDK](chat-room-add-in-application-in-lync-sdk.md)

  - [Chat rooms](chat-rooms.md)

  - [Room manager](room-manager.md)

  - [Chat room messages](chat-room-messages.md)

## Additional resources

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

  - [Beyond the basics: Persistent Chat](beyond-the-basics-persistent-chat.md)

