---
title: ContactAvailability enumeration (Microsoft.Lync.Model)
TOCTitle: ContactAvailability enumeration
ms:assetid: T:Microsoft.Lync.Model.ContactAvailability_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactavailability_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601786
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactAvailability.Busy
- Microsoft.Lync.Model.ContactAvailability
- Microsoft.Lync.Model.ContactAvailability.Free
- Microsoft.Lync.Model.ContactAvailability.Invalid
- Microsoft.Lync.Model.ContactAvailability.Offline
- Microsoft.Lync.Model.ContactAvailability.BusyIdle
- Microsoft.Lync.Model.ContactAvailability.None
- Microsoft.Lync.Model.ContactAvailability.DoNotDisturb
- Microsoft.Lync.Model.ContactAvailability.TemporarilyAway
- Microsoft.Lync.Model.ContactAvailability.FreeIdle
- Microsoft.Lync.Model.ContactAvailability.Away
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactAvailability enumeration

Defines known availability types.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ContactAvailability
'Usage
Dim instance As ContactAvailability
```

``` csharp
public enum ContactAvailability
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
<td>A flag indicating that the contact state is unspecified. An application must not set this flag.</td>
</tr>
<tr class="even">
<td></td>
<td>Free</td>
<td>A flag indicating that the contact is available.</td>
</tr>
<tr class="odd">
<td></td>
<td>FreeIdle</td>
<td>idle states are machine state and can not be published as user state.</td>
</tr>
<tr class="even">
<td></td>
<td>Busy</td>
<td>A flag indicating that the contact is busy and inactive.</td>
</tr>
<tr class="odd">
<td></td>
<td>BusyIdle</td>
<td>idle states are machine state and can not be published as user state.</td>
</tr>
<tr class="even">
<td></td>
<td>DoNotDisturb</td>
<td>A flag indicating that the contact does not want to be disturbed.</td>
</tr>
<tr class="odd">
<td></td>
<td>TemporarilyAway</td>
<td>A flag indicating that the contact is temporarily un-alertable.</td>
</tr>
<tr class="even">
<td></td>
<td>Away</td>
<td>A flag indicating that the contact cannot be alerted.</td>
</tr>
<tr class="odd">
<td></td>
<td>Offline</td>
<td>A flag indicating that the contact is not available.</td>
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

