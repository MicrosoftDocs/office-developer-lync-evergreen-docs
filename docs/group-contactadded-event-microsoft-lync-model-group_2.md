---
title: Group.ContactAdded event (Microsoft.Lync.Model.Group)
TOCTitle: ContactAdded event
ms:assetid: E:Microsoft.Lync.Model.Group.Group.ContactAdded_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.group.contactadded_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590016
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.Group.ContactAdded
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Group.ContactAdded event

Occurs when a contact is added to a group.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ContactAdded As EventHandler(Of GroupMemberChangedEventArgs)
'Usage
Dim instance As Group
Dim handler As EventHandler(Of GroupMemberChangedEventArgs)

AddHandler instance.ContactAdded, handler
```

``` csharp
public event EventHandler<GroupMemberChangedEventArgs> ContactAdded
```

## See also

#### Reference

[Group class](group-class-microsoft-lync-model-group_2.md)

[Group members](group-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

