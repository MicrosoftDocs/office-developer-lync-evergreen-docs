---
title: ShareableContentType enumeration (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ShareableContentType enumeration
ms:assetid: T:Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.shareablecontenttype_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595377
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType.Invalid
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType.NativeFile
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType.PowerPoint
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType.Reserved1
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType.Reserved2
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType.Unsupported
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType.Whiteboard
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType.Qna
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ShareableContentType enumeration

Enumerates supported content types

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ShareableContentType
'Usage
Dim instance As ShareableContentType
```

``` csharp
public enum ShareableContentType
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
<td>Unsupported</td>
<td>Unsupported content.</td>
</tr>
<tr class="even">
<td></td>
<td>PowerPoint</td>
<td>PowerPoint content.</td>
</tr>
<tr class="odd">
<td></td>
<td>Whiteboard</td>
<td>Whiteboarding content.
<p>Be sure to save any whiteboard annotations to a local file before disconnecting the conversation ContentSharingModality. Otherwise, any annotations are lost when you reconnect the modality in the conversation.</p></td>
</tr>
<tr class="even">
<td></td>
<td>NativeFile</td>
<td>Native file attachment.</td>
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
<td>Qna</td>
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

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

