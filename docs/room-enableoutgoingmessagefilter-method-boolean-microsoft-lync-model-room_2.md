---
title: Room.EnableOutgoingMessageFilter method (Boolean) (Microsoft.Lync.Model.Room)
TOCTitle: EnableOutgoingMessageFilter method (Boolean)
ms:assetid: M:Microsoft.Lync.Model.Room.Room.EnableOutgoingMessageFilter(System.Boolean)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.enableoutgoingmessagefilter(v=office.15)
ms:contentKeyID: 48592377
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Room.EnableOutgoingMessageFilter method (Boolean)

Enable the outgoing message filter.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub EnableOutgoingMessageFilter ( _
    noWarning As Boolean _
)
'Usage
Dim instance As Room
Dim noWarning As Boolean

instance.EnableOutgoingMessageFilter(noWarning)
```

``` csharp
public void EnableOutgoingMessageFilter(
    bool noWarning
)
```

#### Parameters

  - noWarning  
    Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## Remarks

By default, a warning is generated each time a message is modified by a filter before being sent. To disable the warning, use the EnableOutgoingMessageFilter(false) override.

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[EnableOutgoingMessageFilter overload](room-enableoutgoingmessagefilter-method-microsoft-lync-model-room_4.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

