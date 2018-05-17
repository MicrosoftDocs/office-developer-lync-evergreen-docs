---
title: ContentSharingModality.ContentRemoved event (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ContentRemoved event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.ContentRemoved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.contentsharingmodality.contentremoved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600542
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.ContentRemoved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContentSharingModality.ContentRemoved event

Raised when an existing ShareableContent has been removed from the content collection of the ContentSharingModality.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ContentRemoved As EventHandler(Of ContentCollectionChangedEventArgs)
'Usage
Dim instance As ContentSharingModality
Dim handler As EventHandler(Of ContentCollectionChangedEventArgs)

AddHandler instance.ContentRemoved, handler
```

``` csharp
public event EventHandler<ContentCollectionChangedEventArgs> ContentRemoved
```

## See also

#### Reference

[ContentSharingModality class](contentsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ContentSharingModality members](contentsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

