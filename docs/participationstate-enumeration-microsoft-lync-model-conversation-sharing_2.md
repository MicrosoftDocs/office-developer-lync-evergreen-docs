---
title: ParticipationState enumeration (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ParticipationState enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.Sharing.ParticipationState_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.participationstate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591708
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ParticipationState
- Microsoft.Lync.Model.Conversation.Sharing.ParticipationState.Controlling
- Microsoft.Lync.Model.Conversation.Sharing.ParticipationState.Invalid
- Microsoft.Lync.Model.Conversation.Sharing.ParticipationState.None
- Microsoft.Lync.Model.Conversation.Sharing.ParticipationState.RequestingControl
- Microsoft.Lync.Model.Conversation.Sharing.ParticipationState.Sharing
- Microsoft.Lync.Model.Conversation.Sharing.ParticipationState.Viewing
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ParticipationState enumeration

Enumerates the participation states of a conversation participant who is sharing or viewing a shared resource.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ParticipationState
'Usage
Dim instance As ParticipationState
```

``` csharp
public enum ParticipationState
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
<td>No one is sharing.</td>
</tr>
<tr class="even">
<td></td>
<td>Viewing</td>
<td>The participant is viewing resources shared by another participant.</td>
</tr>
<tr class="odd">
<td></td>
<td>RequestingControl</td>
<td>The participant is requesting control of the shared resources.</td>
</tr>
<tr class="even">
<td></td>
<td>Controlling</td>
<td>The participant is controlling the shared resources.</td>
</tr>
<tr class="odd">
<td></td>
<td>Sharing</td>
<td>The participant is sharing some resources.</td>
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

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

