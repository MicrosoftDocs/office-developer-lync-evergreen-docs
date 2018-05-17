---
title: RoomPropertyDictionary.GetEnumerator method  (Microsoft.Lync.Model.Room)
TOCTitle: 'GetEnumerator method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomPropertyDictionary.GetEnumerator_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roompropertydictionary.getenumerator_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591127
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomPropertyDictionary.GetEnumerator
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomPropertyDictionary.GetEnumerator method

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetEnumerator As IEnumerator(Of KeyValuePair(Of RoomProperty, Object))
'Usage
Dim instance As RoomPropertyDictionary
Dim returnValue As IEnumerator(Of KeyValuePair(Of RoomProperty, Object))

returnValue = instance.GetEnumerator()
```

``` csharp
public IEnumerator<KeyValuePair<RoomProperty, Object>> GetEnumerator()
```

#### Return value

Type: [System.Collections.Generic.IEnumerator](http://msdn2.microsoft.com/en-us/library/78dfe2yb)\<[KeyValuePair](http://msdn2.microsoft.com/en-us/library/5tbh8a42)\<[RoomProperty](roomproperty-enumeration-microsoft-lync-model-room_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>\>  

#### Implements

[IEnumerable\<T\>.GetEnumerator()](http://msdn2.microsoft.com/en-us/library/s793z9y2)  

## See also

#### Reference

[RoomPropertyDictionary class](roompropertydictionary-class-microsoft-lync-model-room_2.md)

[RoomPropertyDictionary members](roompropertydictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

