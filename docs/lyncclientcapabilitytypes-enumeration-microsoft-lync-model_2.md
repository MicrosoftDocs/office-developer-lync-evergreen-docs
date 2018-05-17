---
title: LyncClientCapabilityTypes enumeration (Microsoft.Lync.Model)
TOCTitle: LyncClientCapabilityTypes enumeration
ms:assetid: T:Microsoft.Lync.Model.LyncClientCapabilityTypes_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclientcapabilitytypes_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601937
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.LyncClientCapabilityTypes.ApplicationSharing
- Microsoft.Lync.Model.LyncClientCapabilityTypes.Text
- Microsoft.Lync.Model.LyncClientCapabilityTypes.IsfInk
- Microsoft.Lync.Model.LyncClientCapabilityTypes.GifInk
- Microsoft.Lync.Model.LyncClientCapabilityTypes.RemoteCallControl
- Microsoft.Lync.Model.LyncClientCapabilityTypes.Cccp
- Microsoft.Lync.Model.LyncClientCapabilityTypes
- Microsoft.Lync.Model.LyncClientCapabilityTypes.Calendar
- Microsoft.Lync.Model.LyncClientCapabilityTypes.Breakthrough
- Microsoft.Lync.Model.LyncClientCapabilityTypes.UserActivity
- Microsoft.Lync.Model.LyncClientCapabilityTypes.Audio
- Microsoft.Lync.Model.LyncClientCapabilityTypes.Invalid
- Microsoft.Lync.Model.LyncClientCapabilityTypes.Video
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncClientCapabilityTypes enumeration

Enumerates the capabilities that for preferred client.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration LyncClientCapabilityTypes
'Usage
Dim instance As LyncClientCapabilityTypes
```

``` csharp
[FlagsAttribute]
public enum LyncClientCapabilityTypes
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
<td>UserActivity</td>
<td>Indicates that the endpoint is the most active one.</td>
</tr>
<tr class="even">
<td></td>
<td>Text</td>
<td>Indicates that the endpoint supports the Instant Messaging.</td>
</tr>
<tr class="odd">
<td></td>
<td>GifInk</td>
<td>Indicates that the endpoint supports the GifInk formats in IM.</td>
</tr>
<tr class="even">
<td></td>
<td>IsfInk</td>
<td>Indicates that the endpoint supports the Ink serialized formats in IM.</td>
</tr>
<tr class="odd">
<td></td>
<td>Audio</td>
<td>Indicates that the endpoint supports voice.</td>
</tr>
<tr class="even">
<td></td>
<td>Video</td>
<td>Indicates that the endpoint supports video.</td>
</tr>
<tr class="odd">
<td></td>
<td>Cccp</td>
<td>Indicates that the endpoint supports the Centralized Conferencing Control Protocol.</td>
</tr>
<tr class="even">
<td></td>
<td>Calendar</td>
<td>Indicates that the endpoint supports publishing the calendar data.</td>
</tr>
<tr class="odd">
<td></td>
<td>RemoteCallControl</td>
<td>Indicates that the endpoint supports the GifInk formats in the Instant Messaging.</td>
</tr>
<tr class="even">
<td></td>
<td>Breakthrough</td>
<td>Indicates that the endpoint supports the remote call control.</td>
</tr>
<tr class="odd">
<td></td>
<td>ApplicationSharing</td>
<td>Indicates that the endpoint supports application sharing.</td>
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

