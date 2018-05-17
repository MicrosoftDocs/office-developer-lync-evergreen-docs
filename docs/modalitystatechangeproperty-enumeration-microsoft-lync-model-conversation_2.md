---
title: ModalityStateChangeProperty enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ModalityStateChangeProperty enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modalitystatechangeproperty_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600930
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved12
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved16
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved30
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved5
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved25
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved11
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.TransferTargetParticipant
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved26
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved1
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved17
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved23
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved7
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.ForwardHistoryInfo
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.IsAutoAccepted
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved6
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved10
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.AlsoRingingOthers
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.InvitingDevice
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved19
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved8
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved9
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved2
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved20
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved24
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved21
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved3
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.AllowedRedirection
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.AcceptingEndpoint
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved15
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved13
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Invalid
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved27
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved22
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved14
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.TransferTargetEndpoint
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved18
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved28
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved29
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.AcceptingParticipant
- Microsoft.Lync.Model.Conversation.ModalityStateChangeProperty.Reserved4
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ModalityStateChangeProperty enumeration

Enumerates the modality state change properties.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ModalityStateChangeProperty
'Usage
Dim instance As ModalityStateChangeProperty
```

``` csharp
public enum ModalityStateChangeProperty
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
<td>ForwardHistoryInfo</td>
<td>Routing history details provided during state change to forwarding.</td>
</tr>
<tr class="even">
<td></td>
<td>AcceptingParticipant</td>
<td>When state change to disconnected because accepted by other party, the accepting participant's contact object.</td>
</tr>
<tr class="odd">
<td></td>
<td>AcceptingEndpoint</td>
<td>When state change to disconnected because accepted by other party, the accepting participant endpoint's uri.</td>
</tr>
<tr class="even">
<td></td>
<td>TransferTargetParticipant</td>
<td>When state change result of transfer, the target participant's contact object.</td>
</tr>
<tr class="odd">
<td></td>
<td>TransferTargetEndpoint</td>
<td>When state change result of transfer, the target participant endpoint's uri.</td>
</tr>
<tr class="even">
<td></td>
<td>AlsoRingingOthers</td>
<td>Routing history details provided when receiving a call as team leader or boss.</td>
</tr>
<tr class="odd">
<td></td>
<td>IsAutoAccepted</td>
<td>Returns true if the call has been auto-accepted.</td>
</tr>
<tr class="even">
<td></td>
<td>AllowedRedirection</td>
<td>Flag indicating if the allowed redirection types of the related modality (value is mask of type RedirectionTypes).</td>
</tr>
<tr class="odd">
<td></td>
<td>InvitingDevice</td>
<td>The inviting device.</td>
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
<td>Reserved3</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved4</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved5</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved6</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved7</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved8</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved9</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved10</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved11</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved12</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved13</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved14</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved15</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved16</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved17</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved18</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved19</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved20</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved21</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved22</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved23</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved24</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved25</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved26</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved27</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved28</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved29</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved30</td>
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

