---
title: PopupPlacementMode enumeration (Microsoft.Lync.Controls)
TOCTitle: PopupPlacementMode enumeration
ms:assetid: T:Microsoft.Lync.Controls.PopupPlacementMode_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.popupplacementmode_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48602038
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.PopupPlacementMode
- Microsoft.Lync.Controls.PopupPlacementMode.Left
- Microsoft.Lync.Controls.PopupPlacementMode.LeftAndVerticallyCentered
- Microsoft.Lync.Controls.PopupPlacementMode.Top
dev_langs:
- CSharp
- JScript
- VB
- other
---

# PopupPlacementMode enumeration

Reserved for internal use. Specifies the relative position in which to display a popup contact card.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Enumeration PopupPlacementMode
'Usage
Dim instance As PopupPlacementMode
```

``` csharp
public enum PopupPlacementMode
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
<td>Top</td>
<td>By default, put the card above the Placement target and align their left edges. If there is no room above, move it below</td>
</tr>
<tr class="even">
<td></td>
<td>Left</td>
<td>By default, put the card to the left of the Placement target and align their bottom edges. If there is no room left, move it right</td>
</tr>
<tr class="odd">
<td></td>
<td>LeftAndVerticallyCentered</td>
<td>By default, put the card to the left of the Placement target and align the middle of the card and the <strong>[PlacementTarget]</strong>. If there is no room left, move it right</td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

