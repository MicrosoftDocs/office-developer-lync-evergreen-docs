---
title: RedirectionTypes enumeration (Microsoft.Lync.Model)
TOCTitle: RedirectionTypes enumeration
ms:assetid: T:Microsoft.Lync.Model.RedirectionTypes_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.redirectiontypes_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48588615
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.RedirectionTypes
- Microsoft.Lync.Model.RedirectionTypes.ForwardToContact
- Microsoft.Lync.Model.RedirectionTypes.ForwardToVoiceMail
- Microsoft.Lync.Model.RedirectionTypes.Invalid
- Microsoft.Lync.Model.RedirectionTypes.None
- Microsoft.Lync.Model.RedirectionTypes.ReplyWithAudioVideo
- Microsoft.Lync.Model.RedirectionTypes.ReplyWithInstantMessage
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RedirectionTypes enumeration

Enumerates the various types of redirection.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration RedirectionTypes
'Usage
Dim instance As RedirectionTypes
```

``` csharp
[FlagsAttribute]
public enum RedirectionTypes
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
<td>No redirection.</td>
</tr>
<tr class="even">
<td></td>
<td>ReplyWithInstantMessage</td>
<td>Redirect by replying with instant message.</td>
</tr>
<tr class="odd">
<td></td>
<td>ReplyWithAudioVideo</td>
<td>Redirect by replying with audio or audio/video.</td>
</tr>
<tr class="even">
<td></td>
<td>ForwardToVoiceMail</td>
<td>Redirect to voicemail.</td>
</tr>
<tr class="odd">
<td></td>
<td>ForwardToContact</td>
<td>Redirect to other contact.</td>
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

