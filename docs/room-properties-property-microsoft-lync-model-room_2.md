---
title: Room.Properties property  (Microsoft.Lync.Model.Room)
TOCTitle: 'Properties property '
ms:assetid: P:Microsoft.Lync.Model.Room.Room.Properties_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.properties_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598691
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.Properties
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.Properties property

Gets a collection of room properties.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Properties As IDictionary(Of RoomProperty, Object)
    Get
'Usage
Dim instance As Room
Dim value As IDictionary(Of RoomProperty, Object)

value = instance.Properties
```

``` csharp
public IDictionary<RoomProperty, Object> Properties { get; }
```

#### Property value

Type: [System.Collections.Generic.IDictionary](http://msdn2.microsoft.com/en-us/library/s4ys34ea)\<[RoomProperty](roomproperty-enumeration-microsoft-lync-model-room_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>  

## Remarks

If the Lync client is signed out after you get an instance of Room, then the Properties property is set to null. You should test Properties for a null state or read the LyncClient.State property before attempting to read Properties.

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

