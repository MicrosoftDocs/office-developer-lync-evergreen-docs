---
title: ModalityDisconnectReason enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ModalityDisconnectReason enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ModalityDisconnectReason_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modalitydisconnectreason_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599356
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason.Busy
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason.ReplyOther
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason.None
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason.Decline
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason.DeclineEverywhere
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason.Timeout
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason.NotAcceptableHere
- Microsoft.Lync.Model.Conversation.ModalityDisconnectReason.Invalid
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ModalityDisconnectReason enumeration

Enumerates the modality disconnect reasons.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ModalityDisconnectReason
'Usage
Dim instance As ModalityDisconnectReason
```

``` csharp
public enum ModalityDisconnectReason
```

## Members

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
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
<td>Disconnect to leave currently connected modality.</td>
</tr>
<tr class="even">
<td></td>
<td>Timeout</td>
<td>Disconnect with timeout for incoming p2p.</td>
</tr>
<tr class="odd">
<td></td>
<td>Busy</td>
<td>Disconnect with busy for incoming p2p.</td>
</tr>
<tr class="even">
<td></td>
<td>NotAcceptableHere</td>
<td>Disconnect with not acceptable here.</td>
</tr>
<tr class="odd">
<td></td>
<td>Decline</td>
<td>Disconnect to decline incoming p2p allowing redirection to voicemail.</td>
</tr>
<tr class="even">
<td></td>
<td>DeclineEverywhere</td>
<td>Disconnect to decline incoming p2p everywhere.</td>
</tr>
<tr class="odd">
<td></td>
<td>ReplyOther</td>
<td>Disconnect to decline incoming P2P and reply with different modality.
<p>If this disconnect reason is selected for an incoming AVModality call then the parent Conversation is disconnected and removed. The ConversationManager.ConversationRemoved event is raised.</p></td>
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

