---
title: ShareableContent.Present method  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'Present method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ShareableContent.Present_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.shareablecontent.present_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596752
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContent.Present
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ShareableContent.Present method

Makes this content available to attendees, takes the presenter lock, and makes the content top-most displayed.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub Present
'Usage
Dim instance As ShareableContent

instance.Present()
```

``` csharp
public void Present()
```

## Remarks

When you call ShareeableContent.Present, the shareable content is shown on the content stage of the conversation window, and replaces content currently shared. This method can only be called on content that is added by the local user.

## See also

#### Reference

[ShareableContent class](shareablecontent-class-microsoft-lync-model-conversation-sharing_2.md)

[ShareableContent members](shareablecontent-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

