---
title: ModalityTypes enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ModalityTypes enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ModalityTypes_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modalitytypes_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48593485
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ModalityTypes
- Microsoft.Lync.Model.Conversation.ModalityTypes.AudioVideo
- Microsoft.Lync.Model.Conversation.ModalityTypes.InstantMessage
- Microsoft.Lync.Model.Conversation.ModalityTypes.Invalid
- Microsoft.Lync.Model.Conversation.ModalityTypes.None
- Microsoft.Lync.Model.Conversation.ModalityTypes.Reserved2
- Microsoft.Lync.Model.Conversation.ModalityTypes.Reserved1
- Microsoft.Lync.Model.Conversation.ModalityTypes.ApplicationSharing
- Microsoft.Lync.Model.Conversation.ModalityTypes.ContentSharing
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ModalityTypes enumeration

Enumerates the modality types.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration ModalityTypes
'Usage
Dim instance As ModalityTypes
```

``` csharp
[FlagsAttribute]
public enum ModalityTypes
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
<td>No modalities</td>
</tr>
<tr class="even">
<td></td>
<td>InstantMessage</td>
<td>Instant Messaging Modality</td>
</tr>
<tr class="odd">
<td></td>
<td>AudioVideo</td>
<td>Audio/Video Modality</td>
</tr>
<tr class="even">
<td></td>
<td>ApplicationSharing</td>
<td>Application Sharing Modality</td>
</tr>
<tr class="odd">
<td></td>
<td>ContentSharing</td>
<td>Content Sharing Modality</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved1</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved2</td>
<td></td>
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

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

