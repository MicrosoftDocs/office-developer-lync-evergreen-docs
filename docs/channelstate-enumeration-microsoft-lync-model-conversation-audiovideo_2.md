---
title: ChannelState enumeration (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: ChannelState enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.channelstate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598731
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState.Connecting
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState.Inactive
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState.SendReceive
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState.Send
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState.Receive
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState.None
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState.Notified
- Microsoft.Lync.Model.Conversation.AudioVideo.ChannelState.Invalid
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ChannelState enumeration

Enumerates the media channel states.

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ChannelState
'Usage
Dim instance As ChannelState
```

``` csharp
public enum ChannelState
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
<td>Media channel state is unknown.</td>
</tr>
<tr class="even">
<td></td>
<td>Connecting</td>
<td>Media channel is connecting.</td>
</tr>
<tr class="odd">
<td></td>
<td>Notified</td>
<td>Media channel is notified.</td>
</tr>
<tr class="even">
<td></td>
<td>Send</td>
<td>Media channel is in send only state.</td>
</tr>
<tr class="odd">
<td></td>
<td>Receive</td>
<td>Media channel is in receive only state.</td>
</tr>
<tr class="even">
<td></td>
<td>SendReceive</td>
<td>Media channel can both send and receive.</td>
</tr>
<tr class="odd">
<td></td>
<td>Inactive</td>
<td>Media channel is inactive.</td>
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

