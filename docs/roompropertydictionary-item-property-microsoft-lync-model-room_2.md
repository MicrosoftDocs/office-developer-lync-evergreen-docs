---
title: RoomPropertyDictionary.Item property  (Microsoft.Lync.Model.Room)
TOCTitle: 'Item property '
ms:assetid: P:Microsoft.Lync.Model.Room.RoomPropertyDictionary.Item(Microsoft.Lync.Model.Room.RoomProperty)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roompropertydictionary.item(v=office.15)
ms:contentKeyID: 48601911
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomPropertyDictionary.Item
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomPropertyDictionary.Item property

Given a room property type, returns the related item value.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Default Property Item ( _
    _propertyType As RoomProperty _
) As Object
    Get
    Set
'Usage
Dim instance As RoomPropertyDictionary
Dim _propertyType As RoomProperty
Dim value As Object

value = instance(_propertyType)

instance(_propertyType) = value
```

``` csharp
public Object this[
    RoomProperty _propertyType
] { get; set; }
```

#### Parameters

  - \_propertyType  
    Type: [Microsoft.Lync.Model.Room.RoomProperty](roomproperty-enumeration-microsoft-lync-model-room_2.md)  

#### Property value

Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Implements

[IDictionary\<TKey, TValue\>.Item\[TKey\]](http://msdn2.microsoft.com/en-us/library/zyxt2e2h)  

## See also

#### Reference

[RoomPropertyDictionary class](roompropertydictionary-class-microsoft-lync-model-room_2.md)

[RoomPropertyDictionary members](roompropertydictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

