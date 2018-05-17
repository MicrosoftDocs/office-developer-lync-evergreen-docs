---
title: InstantMessageCapabilities enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: InstantMessageCapabilities enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.InstantMessageCapabilities_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.instantmessagecapabilities_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598567
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.InstantMessageCapabilities
- Microsoft.Lync.Model.Conversation.InstantMessageCapabilities.CanRenderGif
- Microsoft.Lync.Model.Conversation.InstantMessageCapabilities.CanRenderHtml
- Microsoft.Lync.Model.Conversation.InstantMessageCapabilities.CanRenderIsf
- Microsoft.Lync.Model.Conversation.InstantMessageCapabilities.Invalid
- Microsoft.Lync.Model.Conversation.InstantMessageCapabilities.SupportMime
- Microsoft.Lync.Model.Conversation.InstantMessageCapabilities.CanRenderRtf
dev_langs:
- CSharp
- JScript
- VB
- other
---

# InstantMessageCapabilities enumeration

Enumerates the InstantMessage Capabilities

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration InstantMessageCapabilities
'Usage
Dim instance As InstantMessageCapabilities
```

``` csharp
[FlagsAttribute]
public enum InstantMessageCapabilities
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
<td>CanRenderIsf</td>
<td>Supports ISF format.</td>
</tr>
<tr class="even">
<td></td>
<td>CanRenderGif</td>
<td>Supports GIF format.</td>
</tr>
<tr class="odd">
<td></td>
<td>CanRenderRtf</td>
<td>Supports RTF format.</td>
</tr>
<tr class="even">
<td></td>
<td>SupportMime</td>
<td>Supports MIME format.</td>
</tr>
<tr class="odd">
<td></td>
<td>CanRenderHtml</td>
<td>Supports hypertext markup language (HTML) format.</td>
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

