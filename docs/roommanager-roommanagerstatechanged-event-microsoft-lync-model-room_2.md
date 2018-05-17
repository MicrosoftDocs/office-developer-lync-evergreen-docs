---
title: RoomManager.RoomManagerStateChanged event (Microsoft.Lync.Model.Room)
TOCTitle: RoomManagerStateChanged event
ms:assetid: E:Microsoft.Lync.Model.Room.RoomManager.RoomManagerStateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommanager.roommanagerstatechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592849
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomManager.RoomManagerStateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomManager.RoomManagerStateChanged event

Raised when the room manager is changing its state.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event RoomManagerStateChanged As EventHandler(Of RoomManagerStateChangedEventArgs)
'Usage
Dim instance As RoomManager
Dim handler As EventHandler(Of RoomManagerStateChangedEventArgs)

AddHandler instance.RoomManagerStateChanged, handler
```

``` csharp
public event EventHandler<RoomManagerStateChangedEventArgs> RoomManagerStateChanged
```

## See also

#### Reference

[RoomManager class](roommanager-class-microsoft-lync-model-room_2.md)

[RoomManager members](roommanager-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

