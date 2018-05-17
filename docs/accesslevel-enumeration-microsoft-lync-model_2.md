---
title: AccessLevel enumeration (Microsoft.Lync.Model)
TOCTitle: AccessLevel enumeration
ms:assetid: T:Microsoft.Lync.Model.AccessLevel_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.accesslevel_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590004
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AccessLevel
- Microsoft.Lync.Model.AccessLevel.Blocked
- Microsoft.Lync.Model.AccessLevel.Colleague
- Microsoft.Lync.Model.AccessLevel.External
- Microsoft.Lync.Model.AccessLevel.Default
- Microsoft.Lync.Model.AccessLevel.Friends
- Microsoft.Lync.Model.AccessLevel.Workgroup
- Microsoft.Lync.Model.AccessLevel.Invalid
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AccessLevel enumeration

Enumerates the access entry levels.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration AccessLevel
'Usage
Dim instance As AccessLevel
```

``` csharp
public enum AccessLevel
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
<td>Default</td>
<td>The access level all users have by default.</td>
</tr>
<tr class="even">
<td></td>
<td>External</td>
<td>The access level of a public user.</td>
</tr>
<tr class="odd">
<td></td>
<td>Colleague</td>
<td>The access level of a user in the same enterprise.</td>
</tr>
<tr class="even">
<td></td>
<td>Workgroup</td>
<td>The access level of users in the same workgroup.</td>
</tr>
<tr class="odd">
<td></td>
<td>Friends</td>
<td>The highest access level, assigned to friends.</td>
</tr>
<tr class="even">
<td></td>
<td>Blocked</td>
<td>The access level assigned to users who have been blocked from accessing contact information.</td>
</tr>
<tr class="odd">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

