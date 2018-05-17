---
title: AlertModeTypes enumeration (Microsoft.Lync.Model)
TOCTitle: AlertModeTypes enumeration
ms:assetid: T:Microsoft.Lync.Model.AlertModeTypes_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.alertmodetypes_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596761
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AlertModeTypes
- Microsoft.Lync.Model.AlertModeTypes.Any
- Microsoft.Lync.Model.AlertModeTypes.Audio
- Microsoft.Lync.Model.AlertModeTypes.Invalid
- Microsoft.Lync.Model.AlertModeTypes.Visual
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AlertModeTypes enumeration

Enumerates the modes of alert events.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration AlertModeTypes
'Usage
Dim instance As AlertModeTypes
```

``` csharp
[FlagsAttribute]
public enum AlertModeTypes
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
<td>Visual</td>
<td>Visual can be used for notification.</td>
</tr>
<tr class="even">
<td></td>
<td>Audio</td>
<td>Audio can be used for notification.</td>
</tr>
<tr class="odd">
<td></td>
<td>Any</td>
<td>Any type that can be used for notification.</td>
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

