---
title: Chat rooms
TOCTitle: Chat rooms
ms:assetid: c1bf3f8c-e294-4fd1-8bb3-615029370f99
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933172(v=office.15)
ms:contentKeyID: 50877309
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Chat rooms

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the Persistent Chat followed room feature as it's implemented in Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p>
<p><strong>In this article</strong><br />
Chat room overview<br />
Chat room types<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Chat room overview

A followed room has two attributes that distinguish it from other rooms hosted on Microsoft Lync Server 2013 Persistent Chat. The membership of a local user’s followed room always includes the local user, and a followed room does not need to be joined to provide an activity feed for new messages.

## Chat room types

All chat rooms are encapsulated by a common [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/library/jj266467\(v=office.15\)) class. Although all chat rooms are encapsulated by the same class, the programming patterns used to interact with chat rooms are different depending on the relationship of the user to the room. For example, a chat room that a user is not a member of does not notify the user of new messages even if your application has registered a handler for the [Room.UnreadMessageCountChanged](https://msdn.microsoft.com/library/jj268191\(v=office.15\)) event.

The following table describes the behavior differences between chat rooms represented by the **Room** class.

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Room action</p></th>
<th><p>Followed chat room</p></th>
<th><p>Member of the chat room</p></th>
<th><p>Auditorium chat room</p></th>
<th><p>Not a member of the chat room</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>BeginJoin method</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>BeginLeave method</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>BeginRetrieveAdditionalMessages method</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>BeginRetrieveLatestMessages method</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>BeginSendMessage method</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X2</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>BeginSendStoryMessage method</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X2</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>DisableOutgoingMessageFilter method</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X2</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>EnableOutgoingMessageFilter method</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X2</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>SendFilteredMessage method</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X2</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>IsSendingMessage event</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X2</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>JoinStateChanged event</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>MessagesReceived event</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ParticipantAdded event</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ParticipantRemoved event</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>PropertyChanged event</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>UnreadMessageCountChanged event</p></td>
<td><p>X</p></td>
<td><p>X1</p></td>
<td><p>X1</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

1 The user must be joined to the room.  
2 The user must be joined to the room and be assigned the Presenter role by an administrator.

## See also

  - [Core concepts: Persistent Chat](core-concepts-persistent-chat.md)

  - [Room manager](room-manager.md)

  - [Chat room messages](chat-room-messages.md)

  - [Chat room add-in application in Lync SDK](chat-room-add-in-application-in-lync-sdk.md)

