---
title: Group.ContactRemoved event (Microsoft.Lync.Model.Group)
TOCTitle: ContactRemoved event
ms:assetid: E:Microsoft.Lync.Model.Group.Group.ContactRemoved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.group.contactremoved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598234
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.Group.ContactRemoved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Group.ContactRemoved event

Occurs when a contact is removed from a group.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ContactRemoved As EventHandler(Of GroupMemberChangedEventArgs)
'Usage
Dim instance As Group
Dim handler As EventHandler(Of GroupMemberChangedEventArgs)

AddHandler instance.ContactRemoved, handler
```

``` csharp
public event EventHandler<GroupMemberChangedEventArgs> ContactRemoved
```

## See also

#### Reference

[Group class](group-class-microsoft-lync-model-group_2.md)

[Group members](group-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

