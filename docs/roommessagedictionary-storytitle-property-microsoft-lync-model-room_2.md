---
title: RoomMessageDictionary.StoryTitle property  (Microsoft.Lync.Model.Room)
TOCTitle: 'StoryTitle property '
ms:assetid: P:Microsoft.Lync.Model.Room.RoomMessageDictionary.StoryTitle_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommessagedictionary.storytitle_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595330
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomMessageDictionary.StoryTitle
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomMessageDictionary.StoryTitle property

The title of a story message.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Property StoryTitle As String
    Get
    Set
'Usage
Dim instance As RoomMessageDictionary
Dim value As String

value = instance.StoryTitle

instance.StoryTitle = value
```

``` csharp
public string StoryTitle { get; set; }
```

#### Property value

Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

## Remarks

This property returns an empty string when the message type is not Story.

## See also

#### Reference

[RoomMessageDictionary class](roommessagedictionary-class-microsoft-lync-model-room_2.md)

[RoomMessageDictionary members](roommessagedictionary-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

