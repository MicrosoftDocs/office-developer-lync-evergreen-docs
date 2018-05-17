---
title: ConversationProperty enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ConversationProperty enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ConversationProperty_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversationproperty_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589999
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceTerminateOnLeave
- Microsoft.Lync.Model.Conversation.ConversationProperty.IsUsbConversation
- Microsoft.Lync.Model.Conversation.ConversationProperty.TransferredBy
- Microsoft.Lync.Model.Conversation.ConversationProperty.Invalid
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved13
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved12
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved8
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceAcceptingParticipant
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferencingLocked
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved11
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved2
- Microsoft.Lync.Model.Conversation.ConversationProperty.Id
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferencingAccessType
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved3
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved10
- Microsoft.Lync.Model.Conversation.ConversationProperty.Subject
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved1
- Microsoft.Lync.Model.Conversation.ConversationProperty.AutoTerminateOnIdle
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceInviterRepresentationInfo
- Microsoft.Lync.Model.Conversation.ConversationProperty.Replaced
- Microsoft.Lync.Model.Conversation.ConversationProperty.CallParkOrbit
- Microsoft.Lync.Model.Conversation.ConversationProperty.Inviter
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved7
- Microsoft.Lync.Model.Conversation.ConversationProperty.AcceptanceState
- Microsoft.Lync.Model.Conversation.ConversationProperty
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved5
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceEscalationResult
- Microsoft.Lync.Model.Conversation.ConversationProperty.FollowUp
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceEscalationProgress
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferencingInvitedModes
- Microsoft.Lync.Model.Conversation.ConversationProperty.RepresentedBy
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved6
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceDisclaimerAccepted
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceAccessInformation
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferencingUri
- Microsoft.Lync.Model.Conversation.ConversationProperty.Importance
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved9
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferencingFirstInstantMessage
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved4
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceDisclaimer
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceJoinDialogCompleted
- Microsoft.Lync.Model.Conversation.ConversationProperty.LastActivityTimeStamp
- Microsoft.Lync.Model.Conversation.ConversationProperty.NumberOfParticipantsRecording
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved14
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved15
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved16
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved17
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceVideoHardMute
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved18
- Microsoft.Lync.Model.Conversation.ConversationProperty.Reserved19
- Microsoft.Lync.Model.Conversation.ConversationProperty.ConferenceInstantMessageMute
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationProperty enumeration

Enumerates the conversation properties.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ConversationProperty
'Usage
Dim instance As ConversationProperty
```

``` csharp
public enum ConversationProperty
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
<td>Id</td>
<td>The conversation identifier.
<p>The Id can change in the life of a Conversation instance. In consequence, this property cannot be relied on to uniquely identify a conversation.</p></td>
</tr>
<tr class="even">
<td></td>
<td>Subject</td>
<td>The conversation subject.</td>
</tr>
<tr class="odd">
<td></td>
<td>Importance</td>
<td>The conversation importance level.</td>
</tr>
<tr class="even">
<td></td>
<td>TransferredBy</td>
<td>If this conversation originated through a transfer, then ID of the conversation that originated transfer.</td>
</tr>
<tr class="odd">
<td></td>
<td>Replaced</td>
<td>If this conversation result of consultative transfer replacement, then Id of the conversation it replaces.</td>
</tr>
<tr class="even">
<td></td>
<td>ConferencingUri</td>
<td>If this conversation is/has ever been in conference, the conference focus uri it is connected/will reconnect to.</td>
</tr>
<tr class="odd">
<td></td>
<td>RepresentedBy</td>
<td>If this conversation is effected by boss/admin retargeting, this provides the representation details.</td>
</tr>
<tr class="even">
<td></td>
<td>ConferenceInviterRepresentationInfo</td>
<td>If this conference conversation is effected by boss/admin retargeting, this provides the representation details.</td>
</tr>
<tr class="odd">
<td></td>
<td>FollowUp</td>
<td>The conversation follow up flag.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved1</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>ConferenceAcceptingParticipant</td>
<td>If this conference conversation is answered by another party, this provides the party's contact object.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved2</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>AcceptanceState</td>
<td>The acceptance state (from local point of view) of this conversation.</td>
</tr>
<tr class="even">
<td></td>
<td>IsUsbConversation</td>
<td>Indicates if the conversation is a USB conversation</td>
</tr>
<tr class="odd">
<td></td>
<td>AutoTerminateOnIdle</td>
<td>Indicates whether the conversation will implicitly terminate when last modality session becomes inactive.
<p>Setting this property to false allows you to reuse a Conversation instance to continue a conversation using the participants originally in the conversation. You call into Connect() on the modality previously assigned to the conversation or you can add an additional modality and connect. When AutoTerminateOnIdle is set to false, you must call into Conversation.End() to terminate a conversation.</p></td>
</tr>
<tr class="even">
<td></td>
<td>ConferenceEscalationProgress</td>
<td>Indicates progression of escalation to conference.</td>
</tr>
<tr class="odd">
<td></td>
<td>ConferenceEscalationResult</td>
<td>Indicates result code of escalation to conference.</td>
</tr>
<tr class="even">
<td></td>
<td>ConferencingInvitedModes</td>
<td>Mask with bits set corresponding to invited types.</td>
</tr>
<tr class="odd">
<td></td>
<td>Inviter</td>
<td>Contact class instance for the person that sent the invitation to the conversation.</td>
</tr>
<tr class="even">
<td></td>
<td>ConferencingLocked</td>
<td>Flag corresponding to whether conference is currently locked.</td>
</tr>
<tr class="odd">
<td></td>
<td>ConferencingFirstInstantMessage</td>
<td>Initial instant message that was sent with the conference invitation, formatted as plain text.</td>
</tr>
<tr class="even">
<td></td>
<td>ConferenceAccessInformation</td>
<td>Conference access information that details accessibility mechanisms for this conference. (ConferenceAccessInfo).</td>
</tr>
<tr class="odd">
<td></td>
<td>ConferencingAccessType</td>
<td>Indicates the current access type of the conference.</td>
</tr>
<tr class="even">
<td></td>
<td>CallParkOrbit</td>
<td>The orbit that is used to retrieve a parked call.</td>
</tr>
<tr class="odd">
<td></td>
<td>ConferenceDisclaimer</td>
<td>Disclaimer title and body.</td>
</tr>
<tr class="even">
<td></td>
<td>ConferenceDisclaimerAccepted</td>
<td>Set to true if the user has accepted the conference disclaimer.</td>
</tr>
<tr class="odd">
<td></td>
<td>ConferenceTerminateOnLeave</td>
<td>Terminate conference when terminating the conversation.</td>
</tr>
<tr class="even">
<td></td>
<td>NumberOfParticipantsRecording</td>
<td>Number of participants recording this conversation.</td>
</tr>
<tr class="odd">
<td></td>
<td>ConferenceJoinDialogCompleted</td>
<td>Application should set this to true after selecting audio device during conference join.</td>
</tr>
<tr class="even">
<td></td>
<td>LastActivityTimeStamp</td>
<td>The time stamp of the last conversation activity.</td>
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
<td>Reserved6</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved7</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved18</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved19</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>ConferenceVideoHardMute</td>
<td>Conference Video Hard Mute</td>
</tr>
<tr class="odd">
<td></td>
<td>ConferenceInstantMessageMute</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved8</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved9</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved10</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved11</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved12</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved13</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved14</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved15</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved16</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved17</td>
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

