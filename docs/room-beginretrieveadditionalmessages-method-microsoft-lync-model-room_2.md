---
title: Room.BeginRetrieveAdditionalMessages method  (Microsoft.Lync.Model.Room)
TOCTitle: 'BeginRetrieveAdditionalMessages method '
ms:assetid: M:Microsoft.Lync.Model.Room.Room.BeginRetrieveAdditionalMessages(System.UInt32,System.UInt32,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.room.beginretrieveadditionalmessages(v=office.15)
ms:contentKeyID: 48601566
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.Room.BeginRetrieveAdditionalMessages
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Room.BeginRetrieveAdditionalMessages method

Retrieve additional messages

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginRetrieveAdditionalMessages ( _
    lastMessageID As UInteger, _
    count As UInteger, _
    roomCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Room
Dim lastMessageID As UInteger
Dim count As UInteger
Dim roomCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginRetrieveAdditionalMessages(lastMessageID, _
    count, roomCallback, state)
```

``` csharp
public IAsyncResult BeginRetrieveAdditionalMessages(
    uint lastMessageID,
    uint count,
    AsyncCallback roomCallback,
    Object state
)
```

#### Parameters

  - lastMessageID  
    Type: [System.UInt32](http://msdn2.microsoft.com/en-us/library/ctys3981)  

<!-- end list -->

  - count  
    Type: [System.UInt32](http://msdn2.microsoft.com/en-us/library/ctys3981)  

<!-- end list -->

  - roomCallback  
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

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

