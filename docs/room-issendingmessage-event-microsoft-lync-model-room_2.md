---
title: Room.IsSendingMessage event (Microsoft.Lync.Model.Room)
TOCTitle: IsSendingMessage event
ms:assetid: E:Microsoft.Lync.Model.Room.Room.IsSendingMessage_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.issendingmessage_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601845
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.IsSendingMessage
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.IsSendingMessage event

Raised when the signed in user has finished typing in the group chat room message typing area or Room.BeginSendMessage has been called and Room.IsOutgoingMessageFilterEnabled returns true.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event IsSendingMessage As EventHandler(Of RoomMessageEventArgs)
'Usage
Dim instance As Room
Dim handler As EventHandler(Of RoomMessageEventArgs)

AddHandler instance.IsSendingMessage, handler
```

``` csharp
public event EventHandler<RoomMessageEventArgs> IsSendingMessage
```

## Remarks

If a user finishes typing a message to be posted to a chat room, your application logic has a chance to review the pending post by catching the IsSendingMessage event and running filter or formatting logic against the message string. If the user's message passes your filter, then post the message to the room by calling SendFilteredMessage with the enumerator RoomMessageFilteringAction.Passed. If the message does not pass your filter, call SendFilteredMessage with the enumerator RoomMessageFilteringAction.Canceled. If the message passes your filter but you reformat the message or replace text, call the method with the RoomMessageFilteringAction.Replaced enumerator.

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

