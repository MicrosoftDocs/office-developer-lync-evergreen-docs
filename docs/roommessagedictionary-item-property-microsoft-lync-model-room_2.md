---
title: RoomMessageDictionary.Item property  (Microsoft.Lync.Model.Room)
TOCTitle: 'Item property '
ms:assetid: P:Microsoft.Lync.Model.Room.RoomMessageDictionary.Item(Microsoft.Lync.Model.Room.RoomMessageFormat)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommessagedictionary.item(v=office.15)
ms:contentKeyID: 48589334
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomMessageDictionary.Item
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomMessageDictionary.Item property

Given a message format, returns the item related value.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Default Property Item ( _
    _key As RoomMessageFormat _
) As Object
    Get
    Set
'Usage
Dim instance As RoomMessageDictionary
Dim _key As RoomMessageFormat
Dim value As Object

value = instance(_key)

instance(_key) = value
```

``` csharp
public Object this[
    RoomMessageFormat _key
] { get; set; }
```

#### Parameters

  - \_key  
    Type: [Microsoft.Lync.Model.Room.RoomMessageFormat](roommessageformat-enumeration-microsoft-lync-model-room_2.md)  

#### Property value

Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

## See also

#### Reference

[RoomMessageDictionary class](roommessagedictionary-class-microsoft-lync-model-room_2.md)

[RoomMessageDictionary members](roommessagedictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

