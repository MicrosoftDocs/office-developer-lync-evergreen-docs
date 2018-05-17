---
title: Room.JoinStateChanged event (Microsoft.Lync.Model.Room)
TOCTitle: JoinStateChanged event
ms:assetid: E:Microsoft.Lync.Model.Room.Room.JoinStateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.joinstatechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599851
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.JoinStateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.JoinStateChanged event

Raised when a room join state is changed.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event JoinStateChanged As EventHandler(Of RoomJoinStateChangedEventArgs)
'Usage
Dim instance As Room
Dim handler As EventHandler(Of RoomJoinStateChangedEventArgs)

AddHandler instance.JoinStateChanged, handler
```

``` csharp
public event EventHandler<RoomJoinStateChangedEventArgs> JoinStateChanged
```

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

