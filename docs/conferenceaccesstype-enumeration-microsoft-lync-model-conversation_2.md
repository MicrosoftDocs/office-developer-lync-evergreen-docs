---
title: ConferenceAccessType enumeration (Microsoft.Lync.Model.Conversation)
TOCTitle: ConferenceAccessType enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.ConferenceAccessType_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conferenceaccesstype_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48602032
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ConferenceAccessType.Invalid
- Microsoft.Lync.Model.Conversation.ConferenceAccessType.Anonymous
- Microsoft.Lync.Model.Conversation.ConferenceAccessType
- Microsoft.Lync.Model.Conversation.ConferenceAccessType.Locked
- Microsoft.Lync.Model.Conversation.ConferenceAccessType.Closed
- Microsoft.Lync.Model.Conversation.ConferenceAccessType.Open
- Microsoft.Lync.Model.Conversation.ConferenceAccessType.Unknown
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConferenceAccessType enumeration

Enumerates the various access levels of a conference.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ConferenceAccessType
'Usage
Dim instance As ConferenceAccessType
```

``` csharp
public enum ConferenceAccessType
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
<td>Unknown</td>
<td>Conference access level is unknown.</td>
</tr>
<tr class="even">
<td></td>
<td>Open</td>
<td>Any user who can be authenticated can join the conference.</td>
</tr>
<tr class="odd">
<td></td>
<td>Closed</td>
<td>Only users specifically invited by the conference organizer may join the conference.</td>
</tr>
<tr class="even">
<td></td>
<td>Anonymous</td>
<td>An anonymous user (without an enterprise identity) is allowed to join the conference</td>
</tr>
<tr class="odd">
<td></td>
<td>Locked</td>
<td>Only the presenter can join the conference.</td>
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

