---
title: Group.CanInvoke method  (Microsoft.Lync.Model.Group)
TOCTitle: 'CanInvoke method '
ms:assetid: M:Microsoft.Lync.Model.Group.Group.CanInvoke(Microsoft.Lync.Model.Group.GroupAction,Microsoft.Lync.Model.Contact)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.group.caninvoke(v=office.15)
ms:contentKeyID: 48601568
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.Group.CanInvoke
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Group.CanInvoke method

Checks if a certain action can be applied to the group.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanInvoke ( _
    action As GroupAction, _
    contact As Contact _
) As Boolean
'Usage
Dim instance As Group
Dim action As GroupAction
Dim contact As Contact
Dim returnValue As Boolean

returnValue = instance.CanInvoke(action, _
    contact)
```

``` csharp
public bool CanInvoke(
    GroupAction action,
    Contact contact
)
```

#### Parameters

  - action  
    Type: [Microsoft.Lync.Model.Group.GroupAction](groupaction-enumeration-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - contact  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## See also

#### Reference

[Group class](group-class-microsoft-lync-model-group_2.md)

[Group members](group-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

