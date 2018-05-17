---
title: Conversation.ActionAvailabilityChanged event (Microsoft.Lync.Model.Conversation)
TOCTitle: ActionAvailabilityChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Conversation.ActionAvailabilityChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.actionavailabilitychanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595728
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.ActionAvailabilityChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.ActionAvailabilityChanged event

Raised when an action availability changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ActionAvailabilityChanged As EventHandler(Of ConversationActionAvailabilityEventArgs)
'Usage
Dim instance As Conversation
Dim handler As EventHandler(Of ConversationActionAvailabilityEventArgs)

AddHandler instance.ActionAvailabilityChanged, handler
```

``` csharp
public event EventHandler<ConversationActionAvailabilityEventArgs> ActionAvailabilityChanged
```

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

