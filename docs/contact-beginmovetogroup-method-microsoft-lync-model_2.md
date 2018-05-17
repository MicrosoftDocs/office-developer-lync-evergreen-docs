---
title: Contact.BeginMoveToGroup method  (Microsoft.Lync.Model)
TOCTitle: 'BeginMoveToGroup method '
ms:assetid: M:Microsoft.Lync.Model.Contact.BeginMoveToGroup(Microsoft.Lync.Model.Group.Group,Microsoft.Lync.Model.Group.Group,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.beginmovetogroup(v=office.15)
ms:contentKeyID: 48602013
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.BeginMoveToGroup
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.BeginMoveToGroup method

Moves this contact from a source group to a target group.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginMoveToGroup ( _
    targetGroup As Group, _
    sourceGroup As Group, _
    contactCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Contact
Dim targetGroup As Group
Dim sourceGroup As Group
Dim contactCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginMoveToGroup(targetGroup, _
    sourceGroup, contactCallback, state)
```

``` csharp
public IAsyncResult BeginMoveToGroup(
    Group targetGroup,
    Group sourceGroup,
    AsyncCallback contactCallback,
    Object state
)
```

#### Parameters

  - targetGroup  
    Type: [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - sourceGroup  
    Type: [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - contactCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

