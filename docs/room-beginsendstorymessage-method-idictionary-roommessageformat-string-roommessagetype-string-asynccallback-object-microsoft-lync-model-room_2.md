---
title: Room.BeginSendStoryMessage method (IDictionary(RoomMessageFormat, String), RoomMessageType, String, AsyncCallback, Object) (Microsoft.Lync.Model.Room)
TOCTitle: BeginSendStoryMessage method (IDictionary(RoomMessageFormat, String), RoomMessageType, String, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Room.Room.BeginSendStoryMessage(System.Collections.Generic.IDictionary{Microsoft.Lync.Model.Room.RoomMessageFormat,System.String},Microsoft.Lync.Model.Room.RoomMessageType,System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.beginsendstorymessage(v=office.15)
ms:contentKeyID: 56371589
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Room.BeginSendStoryMessage method (IDictionary\<RoomMessageFormat, String\>, RoomMessageType, String, AsyncCallback, Object)

Sends a story message in different formats to this room.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSendStoryMessage ( _
    contents As IDictionary(Of RoomMessageFormat, String), _
    type As RoomMessageType, _
    storyTitle As String, _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Room
Dim contents As IDictionary(Of RoomMessageFormat, String)
Dim type As RoomMessageType
Dim storyTitle As String
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSendStoryMessage(contents, _
    type, storyTitle, callback, state)
```

``` csharp
public IAsyncResult BeginSendStoryMessage(
    IDictionary<RoomMessageFormat, string> contents,
    RoomMessageType type,
    string storyTitle,
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

  - storyTitle  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

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

[BeginSendStoryMessage overload](room-beginsendstorymessage-method-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

