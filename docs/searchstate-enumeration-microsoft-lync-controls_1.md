---
title: SearchState enumeration (Microsoft.Lync.Controls)
TOCTitle: SearchState enumeration
ms:assetid: T:Microsoft.Lync.Controls.SearchState_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.searchstate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599420
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.SearchState
- Microsoft.Lync.Controls.SearchState.Cleared
- Microsoft.Lync.Controls.SearchState.Error
- Microsoft.Lync.Controls.SearchState.Finished
- Microsoft.Lync.Controls.SearchState.Searching
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchState enumeration

Enumerates the current state of the search operation.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Enumeration SearchState
'Usage
Dim instance As SearchState
```

``` csharp
public enum SearchState
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
<td>Cleared</td>
<td>Cleared</td>
</tr>
<tr class="even">
<td></td>
<td>Searching</td>
<td>Searching</td>
</tr>
<tr class="odd">
<td></td>
<td>Finished</td>
<td>Finished</td>
</tr>
<tr class="even">
<td></td>
<td>Error</td>
<td>Error</td>
</tr>
</tbody>
</table>


## Remarks

The search control reports its current state using these enumerated values. See [ContactSearch](contactsearch-class-microsoft-lync-controls_1.md), [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md), and [ContactSearchInputBox](contactsearchinputbox-class-microsoft-lync-controls_1.md)

## See also

#### Reference

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

