---
title: RoomMessageDictionary class (Microsoft.Lync.Model.Room)
TOCTitle: RoomMessageDictionary class
ms:assetid: T:Microsoft.Lync.Model.Room.RoomMessageDictionary_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommessagedictionary_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594864
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomMessageDictionary
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomMessageDictionary class

A key/value pairing of a message format enumerator and actual message text.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWLite**  
        Microsoft.Lync.Model.Room.RoomMessageDictionary  

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class RoomMessageDictionary _
    Inherits UCWLite
'Usage
Dim instance As RoomMessageDictionary
```

``` csharp
public class RoomMessageDictionary : UCWLite
```

## Remarks

The RoomMessageDictionary contains a collection of Microsoft.Lync.Model.Room.RoomMessageFormat objects. To send a message to a room, you must add at least one key/value pair where the key is RoomMessageFormat.PlainText. You may also add another key/value pair where the key is RoomMessageFormat.Rtf

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[RoomMessageDictionary members](roommessagedictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

