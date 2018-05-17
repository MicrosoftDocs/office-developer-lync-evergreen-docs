---
title: Room.ParticipantRemoved event (Microsoft.Lync.Model.Room)
TOCTitle: ParticipantRemoved event
ms:assetid: E:Microsoft.Lync.Model.Room.Room.ParticipantRemoved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.participantremoved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592311
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.ParticipantRemoved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.ParticipantRemoved event

Raised when a existing participant is removed.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ParticipantRemoved As EventHandler(Of RoomParticipantsEventArgs)
'Usage
Dim instance As Room
Dim handler As EventHandler(Of RoomParticipantsEventArgs)

AddHandler instance.ParticipantRemoved, handler
```

``` csharp
public event EventHandler<RoomParticipantsEventArgs> ParticipantRemoved
```

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

