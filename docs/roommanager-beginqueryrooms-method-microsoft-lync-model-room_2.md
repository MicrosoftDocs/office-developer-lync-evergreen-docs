---
title: RoomManager.BeginQueryRooms method  (Microsoft.Lync.Model.Room)
TOCTitle: 'BeginQueryRooms method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomManager.BeginQueryRooms(System.String,Microsoft.Lync.Model.Room.RoomSearchModeType,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommanager.beginqueryrooms(v=office.15)
ms:contentKeyID: 48599685
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomManager.BeginQueryRooms
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomManager.BeginQueryRooms method

Query room(s)

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginQueryRooms ( _
    keyword As String, _
    searchType As RoomSearchModeType, _
    roomManagerCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As RoomManager
Dim keyword As String
Dim searchType As RoomSearchModeType
Dim roomManagerCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginQueryRooms(keyword, _
    searchType, roomManagerCallback, _
    state)
```

``` csharp
public IAsyncResult BeginQueryRooms(
    string keyword,
    RoomSearchModeType searchType,
    AsyncCallback roomManagerCallback,
    Object state
)
```

#### Parameters

  - keyword  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - searchType  
    Type: [Microsoft.Lync.Model.Room.RoomSearchModeType](roomsearchmodetype-enumeration-microsoft-lync-model-room_2.md)  

<!-- end list -->

  - roomManagerCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[RoomManager class](roommanager-class-microsoft-lync-model-room_2.md)

[RoomManager members](roommanager-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

