---
title: RoomMessageDictionary.Add method  (Microsoft.Lync.Model.Room)
TOCTitle: 'Add method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomMessageDictionary.Add(Microsoft.Lync.Model.Room.RoomMessageFormat,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommessagedictionary.add(v=office.15)
ms:contentKeyID: 48597714
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomMessageDictionary.Add
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomMessageDictionary.Add method

Add a key/value pair composed of RoomMessageType and the message text as a string.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub Add ( _
    key As RoomMessageFormat, _
    value As Object _
)
'Usage
Dim instance As RoomMessageDictionary
Dim key As RoomMessageFormat
Dim value As Object

instance.Add(key, value)
```

``` csharp
public void Add(
    RoomMessageFormat key,
    Object value
)
```

#### Parameters

  - key  
    Type: [Microsoft.Lync.Model.Room.RoomMessageFormat](roommessageformat-enumeration-microsoft-lync-model-room_2.md)  

<!-- end list -->

  - value  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

## Remarks

You can only add a single message of a given RoomMessageType enumerator. This means that you can add a version of your message in plain text and a version in rich text format (rtf). You must always add a plain text version and rtf version is optiona.

## See also

#### Reference

[RoomMessageDictionary class](roommessagedictionary-class-microsoft-lync-model-room_2.md)

[RoomMessageDictionary members](roommessagedictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

