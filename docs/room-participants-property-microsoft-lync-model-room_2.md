---
title: Room.Participants property  (Microsoft.Lync.Model.Room)
TOCTitle: 'Participants property '
ms:assetid: P:Microsoft.Lync.Model.Room.Room.Participants_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.participants_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601124
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.Participants
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.Participants property

Gets the room participants

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Participants As IList(Of RoomUser)
    Get
'Usage
Dim instance As Room
Dim value As IList(Of RoomUser)

value = instance.Participants
```

``` csharp
public IList<RoomUser> Participants { get; }
```

#### Property value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[RoomUser](roomuser-class-microsoft-lync-model-room_2.md)\>  

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

