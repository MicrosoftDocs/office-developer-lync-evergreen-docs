---
title: ConversationManager.ConversationAdded event (Microsoft.Lync.Model.Conversation)
TOCTitle: ConversationAdded event
ms:assetid: E:Microsoft.Lync.Model.Conversation.ConversationManager.ConversationAdded_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversationmanager.conversationadded_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589335
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ConversationManager.ConversationAdded
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationManager.ConversationAdded event

Raised when a conversation add operation completes.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ConversationAdded As EventHandler(Of ConversationManagerEventArgs)
'Usage
Dim instance As ConversationManager
Dim handler As EventHandler(Of ConversationManagerEventArgs)

AddHandler instance.ConversationAdded, handler
```

``` csharp
public event EventHandler<ConversationManagerEventArgs> ConversationAdded
```

## See also

#### Reference

[ConversationManager class](conversationmanager-class-microsoft-lync-model-conversation_2.md)

[ConversationManager members](conversationmanager-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

