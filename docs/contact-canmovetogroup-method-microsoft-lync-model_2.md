---
title: Contact.CanMoveToGroup method  (Microsoft.Lync.Model)
TOCTitle: 'CanMoveToGroup method '
ms:assetid: M:Microsoft.Lync.Model.Contact.CanMoveToGroup(Microsoft.Lync.Model.Group.Group,Microsoft.Lync.Model.Group.Group)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.canmovetogroup(v=office.15)
ms:contentKeyID: 48589953
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.CanMoveToGroup
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.CanMoveToGroup method

Checks if this contact can be moved from a source group to a target group.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanMoveToGroup ( _
    targetGroup As Group, _
    sourceGroup As Group _
) As Boolean
'Usage
Dim instance As Contact
Dim targetGroup As Group
Dim sourceGroup As Group
Dim returnValue As Boolean

returnValue = instance.CanMoveToGroup(targetGroup, _
    sourceGroup)
```

``` csharp
public bool CanMoveToGroup(
    Group targetGroup,
    Group sourceGroup
)
```

#### Parameters

  - targetGroup  
    Type: [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - sourceGroup  
    Type: [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

