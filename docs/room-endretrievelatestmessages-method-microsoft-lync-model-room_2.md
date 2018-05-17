---
title: Room.EndRetrieveLatestMessages method  (Microsoft.Lync.Model.Room)
TOCTitle: 'EndRetrieveLatestMessages method '
ms:assetid: M:Microsoft.Lync.Model.Room.Room.EndRetrieveLatestMessages(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.endretrievelatestmessages(v=office.15)
ms:contentKeyID: 48592865
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.EndRetrieveLatestMessages
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.EndRetrieveLatestMessages method

Ends the Retrevie latest messages operations

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndRetrieveLatestMessages ( _
    asyncResult As IAsyncResult _
) As IList(Of RoomMessage)
'Usage
Dim instance As Room
Dim asyncResult As IAsyncResult
Dim returnValue As IList(Of RoomMessage)

returnValue = instance.EndRetrieveLatestMessages(asyncResult)
```

``` csharp
public IList<RoomMessage> EndRetrieveLatestMessages(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[RoomMessage](roommessage-class-microsoft-lync-model-room_2.md)\>  

## See also

#### Reference

[Room class](room-class-microsoft-lync-model-room_2.md)

[Room members](room-members-microsoft-lync-model-room_2.md)

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

