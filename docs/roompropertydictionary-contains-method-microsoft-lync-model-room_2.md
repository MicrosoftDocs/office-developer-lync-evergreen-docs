---
title: RoomPropertyDictionary.Contains method  (Microsoft.Lync.Model.Room)
TOCTitle: 'Contains method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomPropertyDictionary.Contains(System.Collections.Generic.KeyValuePair{Microsoft.Lync.Model.Room.RoomProperty,System.Object})_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roompropertydictionary.contains(v=office.15)
ms:contentKeyID: 48591138
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomPropertyDictionary.Contains
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomPropertyDictionary.Contains method

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function Contains ( _
    item As KeyValuePair(Of RoomProperty, Object) _
) As Boolean
'Usage
Dim instance As RoomPropertyDictionary
Dim item As KeyValuePair(Of RoomProperty, Object)
Dim returnValue As Boolean

returnValue = instance.Contains(item)
```

``` csharp
public bool Contains(
    KeyValuePair<RoomProperty, Object> item
)
```

#### Parameters

  - item  
    Type: [System.Collections.Generic.KeyValuePair](http://msdn2.microsoft.com/en-us/library/5tbh8a42)\<[RoomProperty](roomproperty-enumeration-microsoft-lync-model-room_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

#### Implements

[ICollection\<T\>.Contains(T)](http://msdn2.microsoft.com/en-us/library/k5cf1d56)  

## See also

#### Reference

[RoomPropertyDictionary class](roompropertydictionary-class-microsoft-lync-model-room_2.md)

[RoomPropertyDictionary members](roompropertydictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

