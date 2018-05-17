---
title: RoomPropertyDictionary class (Microsoft.Lync.Model.Room)
TOCTitle: RoomPropertyDictionary class
ms:assetid: T:Microsoft.Lync.Model.Room.RoomPropertyDictionary_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roompropertydictionary_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589304
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomPropertyDictionary
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomPropertyDictionary class

A dictionary that contains the properties of a group chat room.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWLite**  
        Microsoft.Lync.Model.Room.RoomPropertyDictionary  

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class RoomPropertyDictionary _
    Inherits UCWLite _
    Implements IDictionary(Of RoomProperty, Object),  _
    ICollection(Of KeyValuePair(Of RoomProperty, Object)), IEnumerable(Of KeyValuePair(Of RoomProperty, Object)),  _
    IEnumerable
'Usage
Dim instance As RoomPropertyDictionary
```

``` csharp
public class RoomPropertyDictionary : UCWLite, 
    IDictionary<RoomProperty, Object>, ICollection<KeyValuePair<RoomProperty, Object>>, 
    IEnumerable<KeyValuePair<RoomProperty, Object>>, IEnumerable
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[RoomPropertyDictionary members](roompropertydictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

