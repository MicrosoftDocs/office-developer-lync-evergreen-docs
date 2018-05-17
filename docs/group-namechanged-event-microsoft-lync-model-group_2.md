---
title: Group.NameChanged event (Microsoft.Lync.Model.Group)
TOCTitle: NameChanged event
ms:assetid: E:Microsoft.Lync.Model.Group.Group.NameChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.group.namechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601957
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.Group.NameChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Group.NameChanged event

Occurs when a group is renamed.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event NameChanged As EventHandler(Of GroupNameChangedEventArgs)
'Usage
Dim instance As Group
Dim handler As EventHandler(Of GroupNameChangedEventArgs)

AddHandler instance.NameChanged, handler
```

``` csharp
public event EventHandler<GroupNameChangedEventArgs> NameChanged
```

## See also

#### Reference

[Group class](group-class-microsoft-lync-model-group_2.md)

[Group members](group-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

