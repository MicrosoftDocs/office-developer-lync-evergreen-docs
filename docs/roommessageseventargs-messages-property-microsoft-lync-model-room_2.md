---
title: RoomMessagesEventArgs.Messages property  (Microsoft.Lync.Model.Room)
TOCTitle: 'Messages property '
ms:assetid: P:Microsoft.Lync.Model.Room.RoomMessagesEventArgs.Messages_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommessageseventargs.messages_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591772
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomMessagesEventArgs.Messages
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomMessagesEventArgs.Messages property

Gets the room messages data.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Messages As IList(Of RoomMessage)
    Get
'Usage
Dim instance As RoomMessagesEventArgs
Dim value As IList(Of RoomMessage)

value = instance.Messages
```

``` csharp
public IList<RoomMessage> Messages { get; }
```

#### Property value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[RoomMessage](roommessage-class-microsoft-lync-model-room_2.md)\>  

## See also

#### Reference

[RoomMessagesEventArgs class](roommessageseventargs-class-microsoft-lync-model-room_2.md)

[RoomMessagesEventArgs members](roommessageseventargs-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

