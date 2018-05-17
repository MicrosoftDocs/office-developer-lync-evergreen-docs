---
title: ConversationManager.ConversationRemoved event (Microsoft.Lync.Model.Conversation)
TOCTitle: ConversationRemoved event
ms:assetid: E:Microsoft.Lync.Model.Conversation.ConversationManager.ConversationRemoved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversationmanager.conversationremoved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601784
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ConversationManager.ConversationRemoved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationManager.ConversationRemoved event

Raised when a conversation remove operation completes.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ConversationRemoved As EventHandler(Of ConversationManagerEventArgs)
'Usage
Dim instance As ConversationManager
Dim handler As EventHandler(Of ConversationManagerEventArgs)

AddHandler instance.ConversationRemoved, handler
```

``` csharp
public event EventHandler<ConversationManagerEventArgs> ConversationRemoved
```

## See also

#### Reference

[ConversationManager class](conversationmanager-class-microsoft-lync-model-conversation_2.md)

[ConversationManager members](conversationmanager-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

