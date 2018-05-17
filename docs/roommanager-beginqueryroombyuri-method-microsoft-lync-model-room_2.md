---
title: RoomManager.BeginQueryRoomByUri method  (Microsoft.Lync.Model.Room)
TOCTitle: 'BeginQueryRoomByUri method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomManager.BeginQueryRoomByUri(System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommanager.beginqueryroombyuri(v=office.15)
ms:contentKeyID: 48599680
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomManager.BeginQueryRoomByUri
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomManager.BeginQueryRoomByUri method

Query a room by its URI.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginQueryRoomByUri ( _
    roomUri As String, _
    roomManagerCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As RoomManager
Dim roomUri As String
Dim roomManagerCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginQueryRoomByUri(roomUri, _
    roomManagerCallback, state)
```

``` csharp
public IAsyncResult BeginQueryRoomByUri(
    string roomUri,
    AsyncCallback roomManagerCallback,
    Object state
)
```

#### Parameters

  - roomUri  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

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

