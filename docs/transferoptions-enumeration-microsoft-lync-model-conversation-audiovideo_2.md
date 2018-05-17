---
title: TransferOptions enumeration (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: TransferOptions enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.transferoptions_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589990
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions
- Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions.DisallowRedirection
- Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions.Invalid
- Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions.None
- Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions.Reserved1
- Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions.Reserved2
dev_langs:
- CSharp
- JScript
- VB
- other
---

# TransferOptions enumeration

Enumerates the transfer options.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration TransferOptions
'Usage
Dim instance As TransferOptions
```

``` csharp
[FlagsAttribute]
public enum TransferOptions
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
<td>Default transfer.</td>
</tr>
<tr class="even">
<td></td>
<td>DisallowRedirection</td>
<td>Prevent redirection from original transfer target.</td>
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
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

