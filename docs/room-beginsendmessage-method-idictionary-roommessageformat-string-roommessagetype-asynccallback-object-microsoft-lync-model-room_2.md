---
title: Room.BeginSendMessage method (IDictionary(RoomMessageFormat, String), RoomMessageType, AsyncCallback, Object) (Microsoft.Lync.Model.Room)
TOCTitle: BeginSendMessage method (IDictionary(RoomMessageFormat, String), RoomMessageType, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Room.Room.BeginSendMessage(System.Collections.Generic.IDictionary{Microsoft.Lync.Model.Room.RoomMessageFormat,System.String},Microsoft.Lync.Model.Room.RoomMessageType,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.beginsendmessage(v=office.15)
ms:contentKeyID: 48595463
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Room.BeginSendMessage method (IDictionary\<RoomMessageFormat, String\>, RoomMessageType, AsyncCallback, Object)

Sends a message in different formats to this room.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSendMessage ( _
    contents As IDictionary(Of RoomMessageFormat, String), _
    type As RoomMessageType, _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Room
Dim contents As IDictionary(Of RoomMessageFormat, String)
Dim type As RoomMessageType
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSendMessage(contents, _
    type, callback, state)
```

``` csharp
public IAsyncResult BeginSendMessage(
    IDictionary<RoomMessageFormat, string> contents,
    RoomMessageType type,
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - contents  
    Type: [System.Collections.Generic.IDictionary](http://msdn2.microsoft.com/en-us/library/s4ys34ea)\<[RoomMessageFormat](roommessageformat-enumeration-microsoft-lync-model-room_2.md), [String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)\>  

<!-- end list -->

  - type  
    Type: [Microsoft.Lync.Model.Room.RoomMessageType](roommessagetype-enumeration-microsoft-lync-model-room_2.md)  

<!-- end list -->

  - callback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[BeginSendMessage overload](room-beginsendmessage-method-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

