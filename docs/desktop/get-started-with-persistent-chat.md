---
title: Get started with Persistent Chat
TOCTitle: Persistent Chat
ms:assetid: 98b3c720-5693-4354-bc96-0ef14f369151
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933122(v=office.15)
ms:contentKeyID: 50877257
ms.date: 07/24/2014
mtps_version: v=office.15
description: Master Microsoft Lync 2013's Persistent Chat features with our comprehensive guide. Learn to create chat rooms, post messages, and develop add-in applications.
---

# Get started with Persistent Chat

Learn about the programming concepts and Microsoft Lync 2013 SDK object model that you use to add Lync 2013 Persistent Chat features to your application.

**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="get-started-with-persistent-chat.md#Start"" class="uri"><img src="images/JJ933215.mod_icon_getstartbox(Office.15).gif"/></a>   <a href="get-started-with-persistent-chat.md#Do" class="uri"><img src="images/JJ933215.mod_icon_dobox(Office.15).gif"/></a>   <a href="get-started-with-persistent-chat.md#Learn" class="uri"><img src="images/JJ933215.mod_icon_startbox(Office.15).gif"/></a></p></td>
</tr>
</tbody>
</table>

## What is Persistent Chat?

The classes in the Persistent Chat [Microsoft.Lync.Model.Room](https://msdn.microsoft.com/library/jj277187\(v=office.15\)) namespace are the building blocks for features that range from chat room activity feeds, through chat room extensions called "add-on" applications, and to complete Persistent Chat room client applications. You can get chat rooms, join chat rooms, read chat room messages, and post chat room messages. You can also catch posts from the local user before they are posted if you need to filter, format, or cancel them.

A chat room add-in allows you to create features such as a bot feed that automatically formats and posts messages to a chat room. It is also possible to create an add-in application that can read the complete history of posts in a room and parse the posts for interesting keywords and concepts.
<a name="Start"></a> 

## Get started with Persistent Chat

The prerequisites for working with Persistent Chat are as follows:

  - Microsoft Lync 2013

  - Sign-in credentials for Microsoft Lync Server 2013

  - Microsoft Lync 2013 SDK

### Persistent Chat essentials

To understand how to work with Persistent Chat, it is important to become familiar with the concepts in the following table.

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
<td><p><a href="core-concepts-persistent-chat.md">Core concepts: Persistent Chat</a></p></td>
<td><p>Lync 2013 implements a set of Persistent Chat features that replace the Lync Server 2010 Group Chat client. Lync 2013 SDK gives you programmatic access to those features through its API.</p></td>
</tr>
<tr class="even">
<td><p><a href="chat-rooms.md">Chat rooms</a></p></td>
<td><p>Learn about the Microsoft Lync Server 2013 Persistent Chat room feature as it is implemented in Lync 2013 SDK.</p></td>
</tr>
<tr class="odd">
<td><p><a href="room-manager.md">Room manager</a></p></td>
<td><p>Learn about the Persistent Chat room manager class, which is part of Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="chat-room-messages.md">Chat room messages</a></p></td>
<td><p>Learn about the programming pattern used with the four Lync 2013 SDK types to read messages posted in a Lync 2013 Persistent Chat room.</p></td>
</tr>
</tbody>
</table>
<a name="Do"></a> 

## What can you do with Persistent Chat?

The following table lists basic tasks for working with Persistent Chat.

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
<td><p><a href="how-to-read-messages-sent-to-a-chat-room.md">How to: Read messages sent to a chat room</a></p></td>
<td><p>Shows the Lync 2013 SDK code that you add to an application window so that a user can read messages as they are posted to a Microsoft Lync 2013 chat room.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-send-a-message-to-a-chat-room.md">How to: Send a message to a chat room</a></p></td>
<td><p>Describes how to post regular and story messages to a Microsoft Lync 2013 Persistent Chat room by using methods in Lync 2013 SDK.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-find-a-chat-room.md">How to: Find a chat room</a></p></td>
<td><p>Shows how to query for a Microsoft Lync 2013 Persistent Chat room by using methods in Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-view-chat-room-participants.md">How to: View chat room participants</a></p></td>
<td><p>Shows how to display and maintain a roster of users who have joined a Lync 2013 chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-filter-an-outgoing-message-from-a-local-user-to-a-chat-room.md">How to: Filter an outgoing message from a local user to a chat room</a></p></td>
<td><p>Shows how to create a client-side ethical/security filter for messages that Microsoft Lync 2013 is posting to a Lync 2013 Persistent Chat room.</p></td>
</tr>
</tbody>
</table>
<a name="Learn"></a> 

## Beyond the basics: Learn more about Persistent Chat

The following table lists advanced concepts for working with Persistent Chat.

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
<td><p><a href="create-an-add-in-for-the-persistent-chat-window.md">Create an add-in for the Persistent Chat window</a></p></td>
<td><p>Learn how to design a Persistent Chat room add-in that displays messages that a Microsoft Unified Communications Managed API (UCMA) bot has posted to the hosting chat room and then filters the pending message posts of the local user.</p></td>
</tr>
<tr class="even">
<td><p><a href="create-a-custom-persistent-chat-client.md">Create a custom Persistent Chat client</a></p></td>
<td><p>Learn about the components of a typical custom Microsoft Lync 2013 Persistent Chat window.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Get started with Lync 2013 SDK](get-started-with-lync-2013-sdk.md)

  - [Core concepts: Persistent Chat](core-concepts-persistent-chat.md)

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

  - [Beyond the basics: Persistent Chat](beyond-the-basics-persistent-chat.md)

