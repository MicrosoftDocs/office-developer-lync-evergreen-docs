---
title: CallUnparkReason enumeration (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: CallUnparkReason enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.callunparkreason_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595431
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason.Abandoned
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason.Ringback
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason.Invalid
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason.None
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason.Retrieved
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason.Disconnected
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason.Unknown
- Microsoft.Lync.Model.Conversation.AudioVideo.CallUnparkReason.Fallback
dev_langs:
- CSharp
- JScript
- VB
- other
---

# CallUnparkReason enumeration

Defines the specific reason why a previously-parked call was unparked.

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration CallUnparkReason
'Usage
Dim instance As CallUnparkReason
```

``` csharp
public enum CallUnparkReason
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
<td>Other reasons.</td>
</tr>
<tr class="even">
<td></td>
<td>Abandoned</td>
<td>The parked call was hung up before being retrieved.</td>
</tr>
<tr class="odd">
<td></td>
<td>Disconnected</td>
<td>The parked call was disconnected.</td>
</tr>
<tr class="even">
<td></td>
<td>Fallback</td>
<td>The parked call was transferred to the configured fallback.</td>
</tr>
<tr class="odd">
<td></td>
<td>Retrieved</td>
<td>The parked call was manually retrieved.</td>
</tr>
<tr class="even">
<td></td>
<td>Ringback</td>
<td>The parked call was auto-transferred back to the parker.</td>
</tr>
<tr class="odd">
<td></td>
<td>Unknown</td>
<td>The reason is unknown.</td>
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

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

