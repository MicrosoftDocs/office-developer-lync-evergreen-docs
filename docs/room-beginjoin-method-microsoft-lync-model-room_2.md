---
title: Room.BeginJoin method  (Microsoft.Lync.Model.Room)
TOCTitle: 'BeginJoin method '
ms:assetid: M:Microsoft.Lync.Model.Room.Room.BeginJoin(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.beginjoin(v=office.15)
ms:contentKeyID: 48596308
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.BeginJoin
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.BeginJoin method

Join this room

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginJoin ( _
    roomCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Room
Dim roomCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginJoin(roomCallback, _
    state)
```

``` csharp
public IAsyncResult BeginJoin(
    AsyncCallback roomCallback,
    Object state
)
```

#### Parameters

  - roomCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

