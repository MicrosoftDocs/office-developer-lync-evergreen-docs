---
title: MediaStreamDirection enumeration (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: MediaStreamDirection enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.AudioVideo.MediaStreamDirection_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.mediastreamdirection_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590531
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.MediaStreamDirection
- Microsoft.Lync.Model.Conversation.AudioVideo.MediaStreamDirection.Invalid
- Microsoft.Lync.Model.Conversation.AudioVideo.MediaStreamDirection.None
- Microsoft.Lync.Model.Conversation.AudioVideo.MediaStreamDirection.Receive
- Microsoft.Lync.Model.Conversation.AudioVideo.MediaStreamDirection.Send
dev_langs:
- CSharp
- JScript
- VB
- other
---

# MediaStreamDirection enumeration

Enumerates the media stream directions.

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration MediaStreamDirection
'Usage
Dim instance As MediaStreamDirection
```

``` csharp
public enum MediaStreamDirection
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
<td>Media stream direction is unknown.</td>
</tr>
<tr class="even">
<td></td>
<td>Send</td>
<td>Media stream is outbound.</td>
</tr>
<tr class="odd">
<td></td>
<td>Receive</td>
<td>Media stream is inbound.</td>
</tr>
<tr class="even">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## Remarks

Do not use this property to determine if a conversation is inbound or started locally. Instead, iterate on the conversation modalities collection and examine the Modality.State property of the InstantMessageModality. If the state of the modality is ModalityState.Notified, then the conversation is inbound.

## See also

#### Reference

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

