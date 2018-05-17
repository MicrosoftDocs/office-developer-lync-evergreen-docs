---
title: RoomPropertyDictionary.TryGetValue method  (Microsoft.Lync.Model.Room)
TOCTitle: 'TryGetValue method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomPropertyDictionary.TryGetValue(Microsoft.Lync.Model.Room.RoomProperty,System.Object@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roompropertydictionary.trygetvalue(v=office.15)
ms:contentKeyID: 48593964
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomPropertyDictionary.TryGetValue
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomPropertyDictionary.TryGetValue method

Tries to find a value for the given key.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function TryGetValue ( _
    propertyType As RoomProperty, _
    <OutAttribute> ByRef itemValue As Object _
) As Boolean
'Usage
Dim instance As RoomPropertyDictionary
Dim propertyType As RoomProperty
Dim itemValue As Object
Dim returnValue As Boolean

returnValue = instance.TryGetValue(propertyType, _
    itemValue)
```

``` csharp
public bool TryGetValue(
    RoomProperty propertyType,
    out Object itemValue
)
```

#### Parameters

  - propertyType  
    Type: [Microsoft.Lync.Model.Room.RoomProperty](roomproperty-enumeration-microsoft-lync-model-room_2.md)  

<!-- end list -->

  - itemValue  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

#### Implements

[IDictionary\<TKey, TValue\>.TryGetValue(TKey, TValue)](http://msdn2.microsoft.com/en-us/library/bb299639)  

## See also

#### Reference

[RoomPropertyDictionary class](roompropertydictionary-class-microsoft-lync-model-room_2.md)

[RoomPropertyDictionary members](roompropertydictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

