---
title: ContactSubscriptionRefreshRate enumeration (Microsoft.Lync.Model)
TOCTitle: ContactSubscriptionRefreshRate enumeration
ms:assetid: T:Microsoft.Lync.Model.ContactSubscriptionRefreshRate_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactsubscriptionrefreshrate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594407
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactSubscriptionRefreshRate
- Microsoft.Lync.Model.ContactSubscriptionRefreshRate.High
- Microsoft.Lync.Model.ContactSubscriptionRefreshRate.Invalid
- Microsoft.Lync.Model.ContactSubscriptionRefreshRate.Low
- Microsoft.Lync.Model.ContactSubscriptionRefreshRate.None
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSubscriptionRefreshRate enumeration

Enumerates contact subscription freshness.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ContactSubscriptionRefreshRate
'Usage
Dim instance As ContactSubscriptionRefreshRate
```

``` csharp
public enum ContactSubscriptionRefreshRate
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
<td>None</td>
<td>Shall not be used by the caller, returned if there is no subscription for the contact data.</td>
</tr>
<tr class="even">
<td></td>
<td>Low</td>
<td>The caller needs low temporal accuracy of contact data.</td>
</tr>
<tr class="odd">
<td></td>
<td>High</td>
<td>The caller needs high temporal accuracy of contact data.</td>
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

