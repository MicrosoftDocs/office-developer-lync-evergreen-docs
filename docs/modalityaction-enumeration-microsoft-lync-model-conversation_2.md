---
title: ModalityAction enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ModalityAction enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ModalityAction_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modalityaction_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589949
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ModalityAction.RemoteTransfer
- Microsoft.Lync.Model.Conversation.ModalityAction.ConsultAndTransfer
- Microsoft.Lync.Model.Conversation.ModalityAction.Reject
- Microsoft.Lync.Model.Conversation.ModalityAction.Accept
- Microsoft.Lync.Model.Conversation.ModalityAction.SetIsTyping
- Microsoft.Lync.Model.Conversation.ModalityAction.Retrieve
- Microsoft.Lync.Model.Conversation.ModalityAction.Connect
- Microsoft.Lync.Model.Conversation.ModalityAction.Invalid
- Microsoft.Lync.Model.Conversation.ModalityAction.SetAudioEndpoint
- Microsoft.Lync.Model.Conversation.ModalityAction.SetProperty
- Microsoft.Lync.Model.Conversation.ModalityAction.LocalTransfer
- Microsoft.Lync.Model.Conversation.ModalityAction.SendInstantMessage
- Microsoft.Lync.Model.Conversation.ModalityAction.Hold
- Microsoft.Lync.Model.Conversation.ModalityAction
- Microsoft.Lync.Model.Conversation.ModalityAction.Forward
- Microsoft.Lync.Model.Conversation.ModalityAction.Disconnect
- Microsoft.Lync.Model.Conversation.ModalityAction.AcceptSharingControlRequest
- Microsoft.Lync.Model.Conversation.ModalityAction.CreateShareableNativeFileOnlyContent
- Microsoft.Lync.Model.Conversation.ModalityAction.CreateShareablePowerPointContent
- Microsoft.Lync.Model.Conversation.ModalityAction.CreateShareableWhiteboardContent
- Microsoft.Lync.Model.Conversation.ModalityAction.DeclineSharingControlRequest
- Microsoft.Lync.Model.Conversation.ModalityAction.GrantSharingControl
- Microsoft.Lync.Model.Conversation.ModalityAction.ReleaseSharingControl
- Microsoft.Lync.Model.Conversation.ModalityAction.RequestSharingControl
- Microsoft.Lync.Model.Conversation.ModalityAction.Reserved1
- Microsoft.Lync.Model.Conversation.ModalityAction.RevokeSharingControl
- Microsoft.Lync.Model.Conversation.ModalityAction.Reserved2
- Microsoft.Lync.Model.Conversation.ModalityAction.CreateShareableQnaContent
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ModalityAction enumeration

Enumerates the modality actions.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ModalityAction
'Usage
Dim instance As ModalityAction
```

``` csharp
public enum ModalityAction
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
<td>Connect</td>
<td>Connect to the conversation with a modality.</td>
</tr>
<tr class="even">
<td></td>
<td>Disconnect</td>
<td>Disconnect a modality from the conversation.</td>
</tr>
<tr class="odd">
<td></td>
<td>SetProperty</td>
<td>Set a conversation modality property.</td>
</tr>
<tr class="even">
<td></td>
<td>Hold</td>
<td>Put a conversation modality on hold.</td>
</tr>
<tr class="odd">
<td></td>
<td>Retrieve</td>
<td>Retrieve a conversation modality.</td>
</tr>
<tr class="even">
<td></td>
<td>Forward</td>
<td>Forward a conversation modality.</td>
</tr>
<tr class="odd">
<td></td>
<td>RemoteTransfer</td>
<td>Transfer a conversation modality.</td>
</tr>
<tr class="even">
<td></td>
<td>ConsultAndTransfer</td>
<td>Transfer a conversation modality into another existing conversation.</td>
</tr>
<tr class="odd">
<td></td>
<td>SendInstantMessage</td>
<td>Send an instant message.</td>
</tr>
<tr class="even">
<td></td>
<td>SetIsTyping</td>
<td>Set the IM composing flag. This indicates that an IM is being typed.</td>
</tr>
<tr class="odd">
<td></td>
<td>SetAudioEndpoint</td>
<td>Set the local endpoint for audio.</td>
</tr>
<tr class="even">
<td></td>
<td>Accept</td>
<td>Accept the modality invitation.</td>
</tr>
<tr class="odd">
<td></td>
<td>Reject</td>
<td>Reject the modality invitation.</td>
</tr>
<tr class="even">
<td></td>
<td>LocalTransfer</td>
<td>Transfer the local participant to another endpoint.</td>
</tr>
<tr class="odd">
<td></td>
<td>RequestSharingControl</td>
<td>Request control of shared resources.
<p>This action is called on the application sharing modality of the local participant.</p></td>
</tr>
<tr class="even">
<td></td>
<td>ReleaseSharingControl</td>
<td>Release control of shared resources.
<p>This action is called on the application sharing modality of the participant that is releasing sharing control. You can only release the control of a resource that the local resource is controlling.</p></td>
</tr>
<tr class="odd">
<td></td>
<td>GrantSharingControl</td>
<td>Grant control of shared resources to another participant.
<p>This action is called on the application sharing modality of the participant whose request for control is granted.</p></td>
</tr>
<tr class="even">
<td></td>
<td>RevokeSharingControl</td>
<td>Revoke control of shared resources.
<p>This action is called on the application sharing modality of the participant whose request for control is revoked.</p></td>
</tr>
<tr class="odd">
<td></td>
<td>AcceptSharingControlRequest</td>
<td>Accept the request to grant sharing control.
<p>This action is called on the application sharing modality of the participant whose request for control is accepted.</p></td>
</tr>
<tr class="even">
<td></td>
<td>DeclineSharingControlRequest</td>
<td>Decline the request to grant sharing control.
<p>This action is called on the application sharing modality of the participant whose request for control is declined.</p></td>
</tr>
<tr class="odd">
<td></td>
<td>CreateShareablePowerPointContent</td>
<td>Create shareable PowerPoint content.</td>
</tr>
<tr class="even">
<td></td>
<td>CreateShareableWhiteboardContent</td>
<td>Create shareable Whiteboard content.</td>
</tr>
<tr class="odd">
<td></td>
<td>CreateShareableNativeFileOnlyContent</td>
<td>Create shareable native file content.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved1</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved2</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>CreateShareableQnaContent</td>
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

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

