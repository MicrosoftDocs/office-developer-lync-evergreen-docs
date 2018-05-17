---
title: RoomMessageDictionary.TryGetValue method  (Microsoft.Lync.Model.Room)
TOCTitle: 'TryGetValue method '
ms:assetid: M:Microsoft.Lync.Model.Room.RoomMessageDictionary.TryGetValue(Microsoft.Lync.Model.Room.RoomMessageFormat,System.Object@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommessagedictionary.trygetvalue(v=office.15)
ms:contentKeyID: 48598396
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomMessageDictionary.TryGetValue
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomMessageDictionary.TryGetValue method

Tries to find a value for the given key.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function TryGetValue ( _
    key As RoomMessageFormat, _
    <OutAttribute> ByRef itemValue As Object _
) As Boolean
'Usage
Dim instance As RoomMessageDictionary
Dim key As RoomMessageFormat
Dim itemValue As Object
Dim returnValue As Boolean

returnValue = instance.TryGetValue(key, _
    itemValue)
```

``` csharp
public bool TryGetValue(
    RoomMessageFormat key,
    out Object itemValue
)
```

#### Parameters

  - key  
    Type: [Microsoft.Lync.Model.Room.RoomMessageFormat](roommessageformat-enumeration-microsoft-lync-model-room_2.md)  

<!-- end list -->

  - itemValue  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[RoomMessageDictionary class](roommessagedictionary-class-microsoft-lync-model-room_2.md)

[RoomMessageDictionary members](roommessagedictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

