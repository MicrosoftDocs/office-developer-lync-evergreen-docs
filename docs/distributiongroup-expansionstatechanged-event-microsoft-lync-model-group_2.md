---
title: DistributionGroup.ExpansionStateChanged event (Microsoft.Lync.Model.Group)
TOCTitle: ExpansionStateChanged event
ms:assetid: E:Microsoft.Lync.Model.Group.DistributionGroup.ExpansionStateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.distributiongroup.expansionstatechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598782
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.DistributionGroup.ExpansionStateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# DistributionGroup.ExpansionStateChanged event

Occurs when the expansion state of a distribution group is changed.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ExpansionStateChanged As EventHandler(Of DistributionGroupExpansionStateChangedEventArgs)
'Usage
Dim instance As DistributionGroup
Dim handler As EventHandler(Of DistributionGroupExpansionStateChangedEventArgs)

AddHandler instance.ExpansionStateChanged, handler
```

``` csharp
public event EventHandler<DistributionGroupExpansionStateChangedEventArgs> ExpansionStateChanged
```

## See also

#### Reference

[DistributionGroup class](distributiongroup-class-microsoft-lync-model-group_2.md)

[DistributionGroup members](distributiongroup-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

