---
title: ParticipantProperty enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ParticipantProperty enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ParticipantProperty_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participantproperty_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599151
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ParticipantProperty.Reserved1
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsLeader
- Microsoft.Lync.Model.Conversation.ParticipantProperty.ParkedCall
- Microsoft.Lync.Model.Conversation.ParticipantProperty.Invalid
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsAuthenticated
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsRecording
- Microsoft.Lync.Model.Conversation.ParticipantProperty.SoftMuteChangeInitiator
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsAnonymous
- Microsoft.Lync.Model.Conversation.ParticipantProperty.Name
- Microsoft.Lync.Model.Conversation.ParticipantProperty.Reserved2
- Microsoft.Lync.Model.Conversation.ParticipantProperty
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsInLobby
- Microsoft.Lync.Model.Conversation.ParticipantProperty.RepresentedBy
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsCallParkService
- Microsoft.Lync.Model.Conversation.ParticipantProperty.ReferredByUri
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsLocked
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsPinned
- Microsoft.Lync.Model.Conversation.ParticipantProperty.IsPresenter
- Microsoft.Lync.Model.Conversation.ParticipantProperty.Reserved3
- Microsoft.Lync.Model.Conversation.ParticipantProperty.Reserved4
- Microsoft.Lync.Model.Conversation.ParticipantProperty.Reserved5
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ParticipantProperty enumeration

Enumerates the participant properties.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ParticipantProperty
'Usage
Dim instance As ParticipantProperty
```

``` csharp
public enum ParticipantProperty
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
<td>RepresentedBy</td>
<td>If remote participant is representing another party, the representation details.</td>
</tr>
<tr class="even">
<td></td>
<td>ReferredByUri</td>
<td>If remote participant was referred by another party, the transferor's URI</td>
</tr>
<tr class="odd">
<td></td>
<td>Name</td>
<td>The participant name.</td>
</tr>
<tr class="even">
<td></td>
<td>IsAnonymous</td>
<td>The participant is Anonymous.</td>
</tr>
<tr class="odd">
<td></td>
<td>IsAuthenticated</td>
<td>The participant is authenticated.</td>
</tr>
<tr class="even">
<td></td>
<td>IsInLobby</td>
<td>The participant is in the lobby.</td>
</tr>
<tr class="odd">
<td></td>
<td>IsLeader</td>
<td>The participant is the leader of the conversation.</td>
</tr>
<tr class="even">
<td></td>
<td>IsCallParkService</td>
<td>The participant is the Call Park Service.</td>
</tr>
<tr class="odd">
<td></td>
<td>ParkedCall</td>
<td>The msParkedCall token used for safe-retrieve.</td>
</tr>
<tr class="even">
<td></td>
<td>SoftMuteChangeInitiator</td>
<td>Gives the reason for the last soft mute property change.</td>
</tr>
<tr class="odd">
<td></td>
<td>IsRecording</td>
<td>The participant is recording.</td>
</tr>
<tr class="even">
<td></td>
<td>IsPresenter</td>
<td>The participant is a presenter in the conversation.
<p>A presenter can share local resources in the conversation.</p></td>
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
<td>IsPinned</td>
<td>The video stream of the participant is pinned to the user's conversation window video gallery.</td>
</tr>
<tr class="even">
<td></td>
<td>IsLocked</td>
<td>A meeting presenter has locked he video stream of the participant in the user's conversation window video gallery.</td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved3</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved4</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved5</td>
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

