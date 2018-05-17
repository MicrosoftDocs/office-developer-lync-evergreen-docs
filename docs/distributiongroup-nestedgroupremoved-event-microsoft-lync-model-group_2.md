---
title: DistributionGroup.NestedGroupRemoved event (Microsoft.Lync.Model.Group)
TOCTitle: NestedGroupRemoved event
ms:assetid: E:Microsoft.Lync.Model.Group.DistributionGroup.NestedGroupRemoved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.distributiongroup.nestedgroupremoved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591795
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.DistributionGroup.NestedGroupRemoved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# DistributionGroup.NestedGroupRemoved event

Occurs when a nested group is removed.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event NestedGroupRemoved As EventHandler(Of GroupCollectionChangedEventArgs)
'Usage
Dim instance As DistributionGroup
Dim handler As EventHandler(Of GroupCollectionChangedEventArgs)

AddHandler instance.NestedGroupRemoved, handler
```

``` csharp
public event EventHandler<GroupCollectionChangedEventArgs> NestedGroupRemoved
```

## See also

#### Reference

[DistributionGroup class](distributiongroup-class-microsoft-lync-model-group_2.md)

[DistributionGroup members](distributiongroup-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

