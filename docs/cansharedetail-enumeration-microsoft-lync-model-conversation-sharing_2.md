---
title: CanShareDetail enumeration (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: CanShareDetail enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.cansharedetail_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598564
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail
- Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail.Allowed
- Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail.CannotConnect
- Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail.DisabledByOrganizerPolicy
- Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail.DisabledByPolicy
- Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail.DisabledByRole
- Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail.Invalid
- Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail.DisabledForOtherReason
dev_langs:
- CSharp
- JScript
- VB
- other
---

# CanShareDetail enumeration

Enumerates the detail of why sharing a particular resource is allowed or not allowed.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration CanShareDetail
'Usage
Dim instance As CanShareDetail
```

``` csharp
public enum CanShareDetail
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
<td>Allowed</td>
<td>Sharing is allowed.</td>
</tr>
<tr class="even">
<td></td>
<td>DisabledByPolicy</td>
<td>Sharing is disabled by admin policy.</td>
</tr>
<tr class="odd">
<td></td>
<td>DisabledByOrganizerPolicy</td>
<td>Sharing is disabled by organizer policy.</td>
</tr>
<tr class="even">
<td></td>
<td>DisabledByRole</td>
<td>Sharing is disabled based on participant role.</td>
</tr>
<tr class="odd">
<td></td>
<td>CannotConnect</td>
<td>Cannot share because a connection to the Lync server cannot be made at this time.</td>
</tr>
<tr class="even">
<td></td>
<td>DisabledForOtherReason</td>
<td>Disabled for some other reason.</td>
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

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

