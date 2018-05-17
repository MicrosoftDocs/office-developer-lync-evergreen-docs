---
title: RoomManager.EndQueryRooms method  (Microsoft.Lync.Model.Room)
TOCTitle: 'EndQueryRooms method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomManager.EndQueryRooms(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommanager.endqueryrooms(v=office.15)
ms:contentKeyID: 48591711
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomManager.EndQueryRooms
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomManager.EndQueryRooms method

Query room(s)

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndQueryRooms ( _
    asyncResult As IAsyncResult _
) As IList(Of Room)
'Usage
Dim instance As RoomManager
Dim asyncResult As IAsyncResult
Dim returnValue As IList(Of Room)

returnValue = instance.EndQueryRooms(asyncResult)
```

``` csharp
public IList<Room> EndQueryRooms(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[Room](room-class-microsoft-lync-model-room_2.md)\>  

## See also

#### Reference

[RoomManager class](roommanager-class-microsoft-lync-model-room_2.md)

[RoomManager members](roommanager-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

