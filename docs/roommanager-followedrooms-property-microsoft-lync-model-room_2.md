---
title: RoomManager.FollowedRooms property  (Microsoft.Lync.Model.Room)
TOCTitle: 'FollowedRooms property '
ms:assetid: P:Microsoft.Lync.Model.Room.RoomManager.FollowedRooms_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommanager.followedrooms_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597121
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomManager.FollowedRooms
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomManager.FollowedRooms property

Returns a collection of followed rooms

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property FollowedRooms As IList(Of Room)
    Get
'Usage
Dim instance As RoomManager
Dim value As IList(Of Room)

value = instance.FollowedRooms
```

``` csharp
public IList<Room> FollowedRooms { get; }
```

#### Property value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[Room](room-class-microsoft-lync-model-room_2.md)\>  

## Remarks

A followed room is a room that is added to the local user's contact list. When a user signs in to Lync, all rooms in the followed room list are automatically entered and the user is visible on the participant roster of each followed room. When the user signs out of Lync, then the user automatically leaves all chat rooms.In addition, you get message posting notification events on every followed room as soon as the user signs in and you register for the appropriate room events.

## See also

#### Reference

[RoomManager class](roommanager-class-microsoft-lync-model-room_2.md)

[RoomManager members](roommanager-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

