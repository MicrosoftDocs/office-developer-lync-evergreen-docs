---
title: SupportedFeatures enumeration (Microsoft.Lync.Model)
TOCTitle: SupportedFeatures enumeration
ms:assetid: T:Microsoft.Lync.Model.SupportedFeatures_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.supportedfeatures_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589283
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SupportedFeatures.PhonePairing
- Microsoft.Lync.Model.SupportedFeatures.ApplicationSharing
- Microsoft.Lync.Model.SupportedFeatures.ApplicationInvite
- Microsoft.Lync.Model.SupportedFeatures.LegacyApplicationSharing
- Microsoft.Lync.Model.SupportedFeatures.Audio
- Microsoft.Lync.Model.SupportedFeatures.None
- Microsoft.Lync.Model.SupportedFeatures.Invalid
- Microsoft.Lync.Model.SupportedFeatures.InstantMessageGif
- Microsoft.Lync.Model.SupportedFeatures.FileTransfer
- Microsoft.Lync.Model.SupportedFeatures.InstantMessageHtml
- Microsoft.Lync.Model.SupportedFeatures.InstantMessageInk
- Microsoft.Lync.Model.SupportedFeatures
- Microsoft.Lync.Model.SupportedFeatures.InstantMessageRtf
- Microsoft.Lync.Model.SupportedFeatures.DelegatorContexts
- Microsoft.Lync.Model.SupportedFeatures.Video
- Microsoft.Lync.Model.SupportedFeatures.InstantMessage
- Microsoft.Lync.Model.SupportedFeatures.Reserved1
- Microsoft.Lync.Model.SupportedFeatures.Reserved10
- Microsoft.Lync.Model.SupportedFeatures.Reserved2
- Microsoft.Lync.Model.SupportedFeatures.Reserved3
- Microsoft.Lync.Model.SupportedFeatures.Reserved4
- Microsoft.Lync.Model.SupportedFeatures.Reserved5
- Microsoft.Lync.Model.SupportedFeatures.Reserved6
- Microsoft.Lync.Model.SupportedFeatures.Reserved7
- Microsoft.Lync.Model.SupportedFeatures.Reserved9
- Microsoft.Lync.Model.SupportedFeatures.Reserved8
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SupportedFeatures enumeration

Enumerates the supported features.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration SupportedFeatures
'Usage
Dim instance As SupportedFeatures
```

``` csharp
[FlagsAttribute]
public enum SupportedFeatures
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
<td>No feature is supported.</td>
</tr>
<tr class="even">
<td></td>
<td>DelegatorContexts</td>
<td>The delegator contexts feature is supported.</td>
</tr>
<tr class="odd">
<td></td>
<td>InstantMessageGif</td>
<td>The Gif format in IM is supported.</td>
</tr>
<tr class="even">
<td></td>
<td>InstantMessageInk</td>
<td>The Ink serialized Format in IM is supported.</td>
</tr>
<tr class="odd">
<td></td>
<td>InstantMessageRtf</td>
<td>The Rtf format in IM is supported.</td>
</tr>
<tr class="even">
<td></td>
<td>InstantMessageHtml</td>
<td>The Html format in IM is supported.</td>
</tr>
<tr class="odd">
<td></td>
<td>PhonePairing</td>
<td>The desk phone pairing feature is supported.</td>
</tr>
<tr class="even">
<td></td>
<td>ApplicationSharing</td>
<td>The application sharing feature is supported.</td>
</tr>
<tr class="odd">
<td></td>
<td>LegacyApplicationSharing</td>
<td>The legacy application sharing feature is supported.</td>
</tr>
<tr class="even">
<td></td>
<td>ApplicationInvite</td>
<td>The application invite feature is supported.</td>
</tr>
<tr class="odd">
<td></td>
<td>Audio</td>
<td>The Voice over Internet Protocol feature is supported.</td>
</tr>
<tr class="even">
<td></td>
<td>FileTransfer</td>
<td>The file transfer feature in IM is supported.</td>
</tr>
<tr class="odd">
<td></td>
<td>Video</td>
<td>The video feature is supported.</td>
</tr>
<tr class="even">
<td></td>
<td>InstantMessage</td>
<td>The Instant Messaging feature is supported.</td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved1</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved2</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved3</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved4</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved5</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved6</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved7</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved8</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved9</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved10</td>
<td></td>
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

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

