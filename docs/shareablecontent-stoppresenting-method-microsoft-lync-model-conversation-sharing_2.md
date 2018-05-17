---
title: ShareableContent.StopPresenting method  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'StopPresenting method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ShareableContent.StopPresenting_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.shareablecontent.stoppresenting_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599363
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContent.StopPresenting
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ShareableContent.StopPresenting method

Takes currently shared content off of the content sharing stage but leaves the content in the content collection

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub StopPresenting
'Usage
Dim instance As ShareableContent

instance.StopPresenting()
```

``` csharp
public void StopPresenting()
```

## Remarks

You can also stop presenting the current content by simply presenting a different content object. In this case, the replaced content is no longer presented, but is still in the conversation content collection. This method can only be called on content that is added by the local participant.

## See also

#### Reference

[ShareableContent class](shareablecontent-class-microsoft-lync-model-conversation-sharing_2.md)

[ShareableContent members](shareablecontent-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

