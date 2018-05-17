---
title: RoomManager.FollowedRoomAdded event (Microsoft.Lync.Model.Room)
TOCTitle: FollowedRoomAdded event
ms:assetid: E:Microsoft.Lync.Model.Room.RoomManager.FollowedRoomAdded_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommanager.followedroomadded_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599810
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomManager.FollowedRoomAdded
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomManager.FollowedRoomAdded event

Raised when a room is added to the user's contact list.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event FollowedRoomAdded As EventHandler(Of FollowedRoomsChangedEventArgs)
'Usage
Dim instance As RoomManager
Dim handler As EventHandler(Of FollowedRoomsChangedEventArgs)

AddHandler instance.FollowedRoomAdded, handler
```

``` csharp
public event EventHandler<FollowedRoomsChangedEventArgs> FollowedRoomAdded
```

## See also

#### Reference

[RoomManager class](roommanager-class-microsoft-lync-model-room_2.md)

[RoomManager members](roommanager-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

