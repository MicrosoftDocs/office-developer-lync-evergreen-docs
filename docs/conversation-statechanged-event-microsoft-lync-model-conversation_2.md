---
title: Conversation.StateChanged event (Microsoft.Lync.Model.Conversation)
TOCTitle: StateChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Conversation.StateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.statechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599829
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.StateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.StateChanged event

Raised when the conversation state changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event StateChanged As EventHandler(Of ConversationStateChangedEventArgs)
'Usage
Dim instance As Conversation
Dim handler As EventHandler(Of ConversationStateChangedEventArgs)

AddHandler instance.StateChanged, handler
```

``` csharp
public event EventHandler<ConversationStateChangedEventArgs> StateChanged
```

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

