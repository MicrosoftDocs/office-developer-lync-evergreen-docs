---
title: RoomMessageEventArgs class (Microsoft.Lync.Model.Room)
TOCTitle: RoomMessageEventArgs class
ms:assetid: T:Microsoft.Lync.Model.Room.RoomMessageEventArgs_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommessageeventargs_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598697
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomMessageEventArgs
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomMessageEventArgs class

Encapsulates the state of the event raised when a local user sends a message to a group chat room.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.EventArgs](http://msdn2.microsoft.com/en-us/library/118wxtk3)  
    Microsoft.Lync.Model.Room.RoomMessageEventArgs  

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class RoomMessageEventArgs _
    Inherits EventArgs
'Usage
Dim instance As RoomMessageEventArgs
```

``` csharp
public class RoomMessageEventArgs : EventArgs
```

## Remarks

When room message filtering is enabled, the IsSendingMessge event is raised when the local user is sending a message to the room. This class instance gives you access to the message that will be sent to the room or canceled after you take the appropriate action on the message. For information about taking action on a message, see Room.SendFilteredMessage(Microsoft.Lync.Model.Room.RoomMessage,Microsoft.Lync.Model.Room.RoomZMessageFilteringAction).

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[RoomMessageEventArgs members](roommessageeventargs-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

