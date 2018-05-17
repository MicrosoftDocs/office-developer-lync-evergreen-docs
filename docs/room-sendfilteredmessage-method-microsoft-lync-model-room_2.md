---
title: Room.SendFilteredMessage method  (Microsoft.Lync.Model.Room)
TOCTitle: 'SendFilteredMessage method '
ms:assetid: M:Microsoft.Lync.Model.Room.Room.SendFilteredMessage(Microsoft.Lync.Model.Room.RoomMessage,Microsoft.Lync.Model.Room.RoomMessageFilteringAction)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.sendfilteredmessage(v=office.15)
ms:contentKeyID: 48588551
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.SendFilteredMessage
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.SendFilteredMessage method

Sends a message that has passed a filter as defined by a custom application.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub SendFilteredMessage ( _
    message As RoomMessage, _
    action As RoomMessageFilteringAction _
)
'Usage
Dim instance As Room
Dim message As RoomMessage
Dim action As RoomMessageFilteringAction

instance.SendFilteredMessage(message, _
    action)
```

``` csharp
public void SendFilteredMessage(
    RoomMessage message,
    RoomMessageFilteringAction action
)
```

#### Parameters

  - message  
    Type: [Microsoft.Lync.Model.Room.RoomMessage](roommessage-class-microsoft-lync-model-room_2.md)  

<!-- end list -->

  - action  
    Type: [Microsoft.Lync.Model.Room.RoomMessageFilteringAction](roommessagefilteringaction-enumeration-microsoft-lync-model-room_2.md)  

## Remarks

If a user finishes typing a message to be posted to a chat room, your application logic has a chance to review the pending post by catching the IsSendingMessage event and running filter or formatting logic against the message string. If the user's message passes your filter, then post the message to the room by calling SendFilteredMessage with the enumerator RoomMessageFilteringAction.Passed. If the message does not pass your filter, call SendFilteredMessage with the enumerator RoomMessageFilteringAction.Canceled. If the message passes your filter but you reformat the message or replace text, call the method with the RoomMessageFilteringAction.Replaced enumerator. Note: If you call SendFilteredMessage multiple times with the same message, an exception is raised by Room.EndSendMessage with each send operation after the first send operation.

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

