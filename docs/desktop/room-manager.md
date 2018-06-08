---
title: Room manager
TOCTitle: Room manager
ms:assetid: 6ff10e45-3171-48b3-8a0b-a75d646bb814
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933081(v=office.15)
ms:contentKeyID: 50877210
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Room manager

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the Microsoft Lync 2013 Persistent Chat room manager class that is part of Microsoft Lync 2013 SDK.



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
Room manager overview<br />
Accessing chat rooms<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Room manager overview

The [Microsoft.Lync.Model.Room.RoomManager](https://msdn.microsoft.com/en-us/library/jj277050\(v=office.15\)) class is the entry point to the Persistent Chat feature in the Lync 2013 API. The class gives you access to any chat room that has been added to Microsoft Lync Server 2013 Persistent Chat in a Microsoft Lync Server 2013 topology. Use the class to get a chat room to post and read messages.

## Accessing chat rooms

The room manager class gives you access to chat rooms in the following ways:

  - Query by room title

  - Query by room URI

  - Followed rooms collection

### Query by room title

When a user types a partial room name in the search bar of the Lync 2013 client, the client performs a query against Lync Server 2013 Persistent Chat using the partial title and returns a list of search results. The rooms in the result list are matched by room title against the query string only. The results can include rooms that the user is already following or rooms that the user is not a member of. Room membership is determined by a chat room administrator and cannot be changed at the client level.

### Query by room URI

If the URI of a chat room is known, you can get the corresponding [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/en-us/library/jj266467\(v=office.15\)) object. The room URI is exposed in the **RoomURI()** property only. You cannot get the room URI from the Lync 2013 client itself. Another application can obtain the **Room** object by either searching for it with a partial room title or obtaining it from a followed room list. When a **Room** object is obtained, the URI can be sent to another user by an IM message or email. An advantage of sending a URI instead of a full room title is that the URI is an unambiguous reference to a specific room.

### Followed rooms collection

The followed room collection is the set of chat rooms selected by the user to receive activity notifications. These are the rooms that your application interacts with most frequently. For this reason, the collection is always provisioned on the local endpoint when a user signs in to Lync 2013. For more information about followed rooms, see [Chat rooms](chat-rooms.md).

## See also

  - [Core concepts: Persistent Chat](core-concepts-persistent-chat.md)

  - [Chat rooms](chat-rooms.md)

  - [Chat room messages](chat-room-messages.md)

  - [Chat room add-in application in Lync SDK](chat-room-add-in-application-in-lync-sdk.md)

