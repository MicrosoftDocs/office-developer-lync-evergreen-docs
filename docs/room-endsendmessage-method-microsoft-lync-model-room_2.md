---
title: Room.EndSendMessage method  (Microsoft.Lync.Model.Room)
TOCTitle: 'EndSendMessage method '
ms:assetid: M:Microsoft.Lync.Model.Room.Room.EndSendMessage(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.endsendmessage(v=office.15)
ms:contentKeyID: 48591196
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.EndSendMessage
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.EndSendMessage method

Ends the SendMessage operation

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndSendMessage ( _
    asyncResult As IAsyncResult _
) As RoomMessage
'Usage
Dim instance As Room
Dim asyncResult As IAsyncResult
Dim returnValue As RoomMessage

returnValue = instance.EndSendMessage(asyncResult)
```

``` csharp
public RoomMessage EndSendMessage(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Room.RoomMessage](roommessage-class-microsoft-lync-model-room_2.md)  

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

