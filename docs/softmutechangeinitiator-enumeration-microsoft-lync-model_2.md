---
title: SoftMuteChangeInitiator enumeration (Microsoft.Lync.Model)
TOCTitle: SoftMuteChangeInitiator enumeration
ms:assetid: T:Microsoft.Lync.Model.SoftMuteChangeInitiator_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.softmutechangeinitiator_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600928
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SoftMuteChangeInitiator
- Microsoft.Lync.Model.SoftMuteChangeInitiator.Invalid
- Microsoft.Lync.Model.SoftMuteChangeInitiator.Join
- Microsoft.Lync.Model.SoftMuteChangeInitiator.Local
- Microsoft.Lync.Model.SoftMuteChangeInitiator.Remote
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SoftMuteChangeInitiator enumeration

Enumerates the possible reasons for the most recent SoftMute state change.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration SoftMuteChangeInitiator
'Usage
Dim instance As SoftMuteChangeInitiator
```

``` csharp
public enum SoftMuteChangeInitiator
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
<td>Local</td>
<td>Initiated by local user action.</td>
</tr>
<tr class="even">
<td></td>
<td>Remote</td>
<td>Initiated by the conference leader or paired deskphone.</td>
</tr>
<tr class="odd">
<td></td>
<td>Join</td>
<td>Joined the conference muted.</td>
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

