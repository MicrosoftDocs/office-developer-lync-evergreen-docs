---
title: ConferenceEscalationProgress enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ConferenceEscalationProgress enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conferenceescalationprogress_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596758
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.Completed
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.NotStarted
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.ConnectedToLobby
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.SchedulingConference
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.ConnectingToConference
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.WaitingForPair
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.AwaitingDisclaimerResponse
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.Invalid
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.Failed
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.JoiningLocalMedia
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.WaitingForPeer
- Microsoft.Lync.Model.Conversation.ConferenceEscalationProgress.AwaitingJoinDialogResponse
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConferenceEscalationProgress enumeration

Enumerates the progressive stages of a conversation's escalation to conference.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ConferenceEscalationProgress
'Usage
Dim instance As ConferenceEscalationProgress
```

``` csharp
public enum ConferenceEscalationProgress
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
<td>NotStarted</td>
<td>The conference has not started yet.</td>
</tr>
<tr class="even">
<td></td>
<td>SchedulingConference</td>
<td>The conference is being scheduled.</td>
</tr>
<tr class="odd">
<td></td>
<td>ConnectingToConference</td>
<td>Connecting to the conference.</td>
</tr>
<tr class="even">
<td></td>
<td>ConnectedToLobby</td>
<td>Connected to the conference lobby.</td>
</tr>
<tr class="odd">
<td></td>
<td>JoiningLocalMedia</td>
<td>Joining the conference media.</td>
</tr>
<tr class="even">
<td></td>
<td>WaitingForPair</td>
<td>The conference escalation is in waiting for the paired device state.</td>
</tr>
<tr class="odd">
<td></td>
<td>WaitingForPeer</td>
<td>The conference escalation is in waiting for the peer state.</td>
</tr>
<tr class="even">
<td></td>
<td>Completed</td>
<td>Conference escalation completed successfully.</td>
</tr>
<tr class="odd">
<td></td>
<td>Failed</td>
<td>Failed to join the conference.</td>
</tr>
<tr class="even">
<td></td>
<td>AwaitingDisclaimerResponse</td>
<td>Waiting for the disclaimer response.</td>
</tr>
<tr class="odd">
<td></td>
<td>AwaitingJoinDialogResponse</td>
<td>Waiting for the join audio dialog response.</td>
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

