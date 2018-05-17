---
title: ContactCapabilities enumeration (Microsoft.Lync.Model)
TOCTitle: ContactCapabilities enumeration
ms:assetid: T:Microsoft.Lync.Model.ContactCapabilities_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactcapabilities_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589310
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactCapabilities.ShowPresence
- Microsoft.Lync.Model.ContactCapabilities.RenderAppShare
- Microsoft.Lync.Model.ContactCapabilities.RenderAudio
- Microsoft.Lync.Model.ContactCapabilities.CaptureAudio
- Microsoft.Lync.Model.ContactCapabilities.CaptureVideo
- Microsoft.Lync.Model.ContactCapabilities
- Microsoft.Lync.Model.ContactCapabilities.RenderVideo
- Microsoft.Lync.Model.ContactCapabilities.Invalid
- Microsoft.Lync.Model.ContactCapabilities.RenderInstantMessage
- Microsoft.Lync.Model.ContactCapabilities.CaptureAppShare
- Microsoft.Lync.Model.ContactCapabilities.CaptureInstantMessage
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactCapabilities enumeration

Defines Contact Capability types.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration ContactCapabilities
'Usage
Dim instance As ContactCapabilities
```

``` csharp
[FlagsAttribute]
public enum ContactCapabilities
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
<td>ShowPresence</td>
<td>A contact presence state can be shown.</td>
</tr>
<tr class="even">
<td></td>
<td>CaptureInstantMessage</td>
<td>A contact can send instant messages.</td>
</tr>
<tr class="odd">
<td></td>
<td>RenderInstantMessage</td>
<td>A contact can receive instant messages.</td>
</tr>
<tr class="even">
<td></td>
<td>CaptureAudio</td>
<td>A contact can send audio.</td>
</tr>
<tr class="odd">
<td></td>
<td>RenderAudio</td>
<td>A contact can receive audio.</td>
</tr>
<tr class="even">
<td></td>
<td>CaptureVideo</td>
<td>A contact can send video.</td>
</tr>
<tr class="odd">
<td></td>
<td>RenderVideo</td>
<td>A contact can receive video.</td>
</tr>
<tr class="even">
<td></td>
<td>CaptureAppShare</td>
<td>A contact can perform application sharing.</td>
</tr>
<tr class="odd">
<td></td>
<td>RenderAppShare</td>
<td>A contact can view application sharing.</td>
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

