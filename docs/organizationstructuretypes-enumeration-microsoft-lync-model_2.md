---
title: OrganizationStructureTypes enumeration (Microsoft.Lync.Model)
TOCTitle: OrganizationStructureTypes enumeration
ms:assetid: T:Microsoft.Lync.Model.OrganizationStructureTypes_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.organizationstructuretypes_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590515
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.OrganizationStructureTypes
- Microsoft.Lync.Model.OrganizationStructureTypes.DirectReports
- Microsoft.Lync.Model.OrganizationStructureTypes.Invalid
- Microsoft.Lync.Model.OrganizationStructureTypes.Managers
- Microsoft.Lync.Model.OrganizationStructureTypes.Peers
dev_langs:
- CSharp
- JScript
- VB
- other
---

# OrganizationStructureTypes enumeration

Enumerates the organizational roles of people in the contact's organization.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration OrganizationStructureTypes
'Usage
Dim instance As OrganizationStructureTypes
```

``` csharp
[FlagsAttribute]
public enum OrganizationStructureTypes
```

## Members

<table>
<thead>
<tr class="header">
<th></th>
<th>Member name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td>Managers</td>
<td>Contact's manager chain.</td>
</tr>
<tr class="even">
<td></td>
<td>Peers</td>
<td>Contact's peers.</td>
</tr>
<tr class="odd">
<td></td>
<td>DirectReports</td>
<td>Contact's direct reports.</td>
</tr>
<tr class="even">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

