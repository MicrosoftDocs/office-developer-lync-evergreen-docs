---
title: AudioPlayBackModes enumeration (Microsoft.Lync.Model.Device)
TOCTitle: AudioPlayBackModes enumeration
ms:assetid: T:Microsoft.Lync.Model.Device.AudioPlayBackModes_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.device.audioplaybackmodes_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601863
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Device.AudioPlayBackModes
- Microsoft.Lync.Model.Device.AudioPlayBackModes.Alert
- Microsoft.Lync.Model.Device.AudioPlayBackModes.Ringing
- Microsoft.Lync.Model.Device.AudioPlayBackModes.Invalid
- Microsoft.Lync.Model.Device.AudioPlayBackModes.Communication
- Microsoft.Lync.Model.Device.AudioPlayBackModes.AlertAndCommunication
- Microsoft.Lync.Model.Device.AudioPlayBackModes.Handset
- Microsoft.Lync.Model.Device.AudioPlayBackModes.None
- Microsoft.Lync.Model.Device.AudioPlayBackModes.SuppressOnDeskphones
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AudioPlayBackModes enumeration

Enumerates AudioFeedback Devices.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model.Device](microsoft-lync-model-device-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration AudioPlayBackModes
'Usage
Dim instance As AudioPlayBackModes
```

``` csharp
[FlagsAttribute]
public enum AudioPlayBackModes
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
<td>Play audio file back through no device.</td>
</tr>
<tr class="even">
<td></td>
<td>Alert</td>
<td>Playback audio through device configured for alert sounds.</td>
</tr>
<tr class="odd">
<td></td>
<td>Communication</td>
<td>Playback audio through device configured for Unified Communications.</td>
</tr>
<tr class="even">
<td></td>
<td>Handset</td>
<td>Playback audio through telephone handset device.</td>
</tr>
<tr class="odd">
<td></td>
<td>Ringing</td>
<td>Playback audio through device configured to play ringing tone.</td>
</tr>
<tr class="even">
<td></td>
<td>AlertAndCommunication</td>
<td>Playback audio through both Lync and alert devices.</td>
</tr>
<tr class="odd">
<td></td>
<td>SuppressOnDeskphones</td>
<td>Suppress playback audio through desk telephone device.</td>
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

[Microsoft.Lync.Model.Device namespace](microsoft-lync-model-device-namespace_2.md)

