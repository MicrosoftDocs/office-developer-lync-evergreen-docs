---
title: ShareableContent.StateChanged event (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: StateChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Sharing.ShareableContent.StateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.shareablecontent.statechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596750
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContent.StateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ShareableContent.StateChanged event

Raised when the state of a ShareableContent object changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event StateChanged As EventHandler(Of ShareableContentStateChangedEventArgs)
'Usage
Dim instance As ShareableContent
Dim handler As EventHandler(Of ShareableContentStateChangedEventArgs)

AddHandler instance.StateChanged, handler
```

``` csharp
public event EventHandler<ShareableContentStateChangedEventArgs> StateChanged
```

## Remarks

Use this event to track the progress of a shareable content item as the content bin upload operation progresses. When the shareable content item is in the content bin and available to present in the conversation, the state of the object is ShareableContentState.Online.

## See also

#### Reference

[ShareableContent class](shareablecontent-class-microsoft-lync-model-conversation-sharing_2.md)

[ShareableContent members](shareablecontent-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

