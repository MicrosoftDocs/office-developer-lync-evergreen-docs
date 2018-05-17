---
title: ShareableContentState enumeration (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ShareableContentState enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.shareablecontentstate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590575
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState.Active
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState.Connecting
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState.Disconnecting
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState.Initializing
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState.Invalid
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState.Offline
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState.Online
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState.Unusable
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ShareableContentState enumeration

Enumerates the states of a shareable content object.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ShareableContentState
'Usage
Dim instance As ShareableContentState
```

``` csharp
public enum ShareableContentState
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
<td>Initializing</td>
<td>The content is in the initializing state.</td>
</tr>
<tr class="even">
<td></td>
<td>Offline</td>
<td>The content has been created, but is not uploaded yet.</td>
</tr>
<tr class="odd">
<td></td>
<td>Connecting</td>
<td>The content is being converted/uploaded, or is being downloaded for viewing.</td>
</tr>
<tr class="even">
<td></td>
<td>Online</td>
<td>The content has been successfully uploaded or downloaded, and is fully functional.</td>
</tr>
<tr class="odd">
<td></td>
<td>Disconnecting</td>
<td>The content is being deleted from the server.</td>
</tr>
<tr class="even">
<td></td>
<td>Active</td>
<td>The content is being presented.</td>
</tr>
<tr class="odd">
<td></td>
<td>Unusable</td>
<td>The content is not usable anymore.</td>
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

