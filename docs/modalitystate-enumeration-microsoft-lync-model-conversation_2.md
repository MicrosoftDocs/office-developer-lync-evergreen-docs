---
title: ModalityState enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ModalityState enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ModalityState_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modalitystate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600629
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ModalityState.ConnectingToCaller
- Microsoft.Lync.Model.Conversation.ModalityState.Notified
- Microsoft.Lync.Model.Conversation.ModalityState.Connected
- Microsoft.Lync.Model.Conversation.ModalityState
- Microsoft.Lync.Model.Conversation.ModalityState.Forwarding
- Microsoft.Lync.Model.Conversation.ModalityState.Disconnected
- Microsoft.Lync.Model.Conversation.ModalityState.Invalid
- Microsoft.Lync.Model.Conversation.ModalityState.Transferring
- Microsoft.Lync.Model.Conversation.ModalityState.OnHold
- Microsoft.Lync.Model.Conversation.ModalityState.Joining
- Microsoft.Lync.Model.Conversation.ModalityState.Connecting
- Microsoft.Lync.Model.Conversation.ModalityState.Suspended
- Microsoft.Lync.Model.Conversation.ModalityState.Disconnecting
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ModalityState enumeration

Enumerates the modality states.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ModalityState
'Usage
Dim instance As ModalityState
```

``` csharp
public enum ModalityState
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
<td>Disconnected</td>
<td>The modality is not part of the conversation.</td>
</tr>
<tr class="even">
<td></td>
<td>Connecting</td>
<td>The invitation is being delivered.</td>
</tr>
<tr class="odd">
<td></td>
<td>Notified</td>
<td>The invitation was delivered and the endpoint was notified.</td>
</tr>
<tr class="even">
<td></td>
<td>Joining</td>
<td>The invitation was accepted and the endpoints are joining.</td>
</tr>
<tr class="odd">
<td></td>
<td>ConnectingToCaller</td>
<td>The modality agent is connecting to the caller.</td>
</tr>
<tr class="even">
<td></td>
<td>Connected</td>
<td>The modality is successfully connected.</td>
</tr>
<tr class="odd">
<td></td>
<td>Suspended</td>
<td>The modality is suspended and has limited capabilities.</td>
</tr>
<tr class="even">
<td></td>
<td>OnHold</td>
<td>The connected modality is placed on hold.</td>
</tr>
<tr class="odd">
<td></td>
<td>Forwarding</td>
<td>The connecting modality is being forwarded.</td>
</tr>
<tr class="even">
<td></td>
<td>Transferring</td>
<td>The connected modality is being transferred.</td>
</tr>
<tr class="odd">
<td></td>
<td>Disconnecting</td>
<td>The modality is being disconnected</td>
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

