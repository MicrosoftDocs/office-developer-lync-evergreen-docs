---
title: MenuContext enumeration (Microsoft.Lync.Controls)
TOCTitle: MenuContext enumeration
ms:assetid: T:Microsoft.Lync.Controls.MenuContext_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.menucontext_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589943
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.MenuContext
- Microsoft.Lync.Controls.MenuContext.ContactListByGroup
- Microsoft.Lync.Controls.MenuContext.ContactListByRelationship
- Microsoft.Lync.Controls.MenuContext.ContactListByStatus
- Microsoft.Lync.Controls.MenuContext.CustomContactList
- Microsoft.Lync.Controls.MenuContext.SearchResult
dev_langs:
- CSharp
- JScript
- VB
- other
---

# MenuContext enumeration

Specifies the context in which a context menu is being used.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Enumeration MenuContext
'Usage
Dim instance As MenuContext
```

``` csharp
public enum MenuContext
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
<td>ContactListByGroup</td>
<td>Specifies the menu context of a ContactsList in group-by-group mode</td>
</tr>
<tr class="even">
<td></td>
<td>ContactListByStatus</td>
<td>Specifies the menu context of a ContactsList in group-by-status mode</td>
</tr>
<tr class="odd">
<td></td>
<td>ContactListByRelationship</td>
<td>Specifies the menu context of a ContactsList in group-by-relationship mode</td>
</tr>
<tr class="even">
<td></td>
<td>CustomContactList</td>
<td>Specifies the menu context of a CustomContactList</td>
</tr>
<tr class="odd">
<td></td>
<td>SearchResult</td>
<td>Specifies the menu context of a ContactSearchResultList list</td>
</tr>
</tbody>
</table>


## Remarks

Specifies the context in which a context menu is being used. See [ContactList](contactlist-class-microsoft-lync-controls_1.md), [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md), or CustomContactList.

## See also

#### Reference

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

