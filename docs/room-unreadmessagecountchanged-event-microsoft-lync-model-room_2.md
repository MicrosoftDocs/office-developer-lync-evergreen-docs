---
title: Room.UnreadMessageCountChanged event (Microsoft.Lync.Model.Room)
TOCTitle: UnreadMessageCountChanged event
ms:assetid: E:Microsoft.Lync.Model.Room.Room.UnreadMessageCountChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.unreadmessagecountchanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592214
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.UnreadMessageCountChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.UnreadMessageCountChanged event

Raised when unread message count changes.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event UnreadMessageCountChanged As EventHandler(Of UnreadMessageCountChangedEventArgs)
'Usage
Dim instance As Room
Dim handler As EventHandler(Of UnreadMessageCountChangedEventArgs)

AddHandler instance.UnreadMessageCountChanged, handler
```

``` csharp
public event EventHandler<UnreadMessageCountChangedEventArgs> UnreadMessageCountChanged
```

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

