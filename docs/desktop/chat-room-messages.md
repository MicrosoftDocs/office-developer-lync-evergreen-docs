---
title: Chat room messages
TOCTitle: Chat room messages
ms:assetid: 3baf2f9e-94f5-4c1c-95ab-68f653fc0f4f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937304(v=office.15)
ms:contentKeyID: 50877132
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Chat room messages

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the programming pattern used with the four Microsoft Lync 2013 SDK types to read messages posted in a Microsoft Lync 2013 Persistent Chat room.



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
Message overview<br />
Retrieving room messages<br />
Room message object model<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Message overview

The [Microsoft.Lync.Model.Room.RoomMessage](https://msdn.microsoft.com/library/jj276207\(v=office.15\)) class encapsulates a message posted in a room. This class is not used to post messages to a room. A **RoomMessage** object has attributes that tell you who posted the message, the room it is posted to, the date and time the message was posted, the ID of the message, and the message text.

## Retrieving room messages

Messages can only be retrieved from instances of the [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/library/jj266467\(v=office.15\)) class to which messages are posted. When a room has been joined or followed, get posted messages by calling asynchronous operations on the room. For information about retrieving room messages, see [How to: Read messages sent to a chat room](how-to-read-messages-sent-to-a-chat-room.md). By registering for the [Room.MessagesReceived](https://msdn.microsoft.com/library/jj277819\(v=office.15\)) event, an application is notified when new messages are received.

## Room message object model

The room message object model is composed of the [Microsoft.Lync.Model.Room.RoomMessage](https://msdn.microsoft.com/library/jj276207\(v=office.15\)) whose attributes include sender and room URIs, ID, and sent time. In addition, the class exposes a property whose value is an object of the [Microsoft.Lync.Model.Room.RoomMessageDictionary](https://msdn.microsoft.com/library/jj275495\(v=office.15\)) class. The message dictionary contains message formatting/message text pairs along with additional message attributes.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>RoomMessageDictionary</strong> does not implement <strong>IDictionary</strong> although it does contain data similar access methods. The <a href="https://msdn.microsoft.com/library/jj275726(v=office.15)">RoomMessageDictionary.StoryTitle</a> property and the <a href="https://msdn.microsoft.com/library/jj276744(v=office.15)">RoomMessageDictionary.Type</a> property have a one-to-one relationship with the room message itself, while the <a href="https://msdn.microsoft.com/library/jj294137(v=office.15)">RoomMessageDictionary.Keys</a> and <a href="https://msdn.microsoft.com/library/jj267961(v=office.15)">RoomMessageDictionary.Values</a> properties return collections and have a one-to-many relationship with the room message.<br />
<br />
The relationships in this object model allow the API to state that a given room message is an alert, regular, or story message while the message has plain text content and RTF content.</p></td>
</tr>
</tbody>
</table>

Figure 1. Chat room message object model

  
![Chat room message class model diagram](images/JJ937304.LyncClientSDK_RoomMessageModel(Office.15).jpg "Chat room message class model diagram")

## See also

  - [Core concepts: Persistent Chat](core-concepts-persistent-chat.md)

  - [Chat rooms](chat-rooms.md)

  - [Room manager](room-manager.md)

  - [Chat room add-in application in Lync SDK](chat-room-add-in-application-in-lync-sdk.md)

