---
title: ContentSharingModality.ContentAdded event (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ContentAdded event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.ContentAdded_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.contentsharingmodality.contentadded_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601087
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.ContentAdded
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContentSharingModality.ContentAdded event

Raised when any conversation participant has added a ShareableContent object to the conversation.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ContentAdded As EventHandler(Of ContentCollectionChangedEventArgs)
'Usage
Dim instance As ContentSharingModality
Dim handler As EventHandler(Of ContentCollectionChangedEventArgs)

AddHandler instance.ContentAdded, handler
```

``` csharp
public event EventHandler<ContentCollectionChangedEventArgs> ContentAdded
```

## Remarks

Be careful about calling the ShareableContent.Present() method on the added ShearableContent object. This event is raised when content is added by any participant, while you can only invoke the Present() method on content added by the local user.

## See also

#### Reference

[ContentSharingModality class](contentsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ContentSharingModality members](contentsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

