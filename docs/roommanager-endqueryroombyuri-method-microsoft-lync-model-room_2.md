---
title: RoomManager.EndQueryRoomByUri method  (Microsoft.Lync.Model.Room)
TOCTitle: 'EndQueryRoomByUri method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomManager.EndQueryRoomByUri(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommanager.endqueryroombyuri(v=office.15)
ms:contentKeyID: 48598705
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomManager.EndQueryRoomByUri
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomManager.EndQueryRoomByUri method

Query a room by its URI.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndQueryRoomByUri ( _
    asyncResult As IAsyncResult _
) As Room
'Usage
Dim instance As RoomManager
Dim asyncResult As IAsyncResult
Dim returnValue As Room

returnValue = instance.EndQueryRoomByUri(asyncResult)
```

``` csharp
public Room EndQueryRoomByUri(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Room.Room](room-class-microsoft-lync-model-room_2.md)  

## See also

#### Reference

[RoomManager class](roommanager-class-microsoft-lync-model-room_2.md)

[RoomManager members](roommanager-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

