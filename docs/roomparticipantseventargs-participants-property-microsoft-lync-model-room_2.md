---
title: RoomParticipantsEventArgs.Participants property  (Microsoft.Lync.Model.Room)
TOCTitle: 'Participants property '
ms:assetid: P:Microsoft.Lync.Model.Room.RoomParticipantsEventArgs.Participants_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roomparticipantseventargs.participants_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601555
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomParticipantsEventArgs.Participants
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomParticipantsEventArgs.Participants property

Get new room participants.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Participants As IList(Of RoomUser)
    Get
'Usage
Dim instance As RoomParticipantsEventArgs
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

[RoomParticipantsEventArgs class](roomparticipantseventargs-class-microsoft-lync-model-room_2.md)

[RoomParticipantsEventArgs members](roomparticipantseventargs-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

