---
title: InstantMessageModality.InstantMessageReceived event (Microsoft.Lync.Model.Conversation)
TOCTitle: InstantMessageReceived event
ms:assetid: E:Microsoft.Lync.Model.Conversation.InstantMessageModality.InstantMessageReceived_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.instantmessagemodality.instantmessagereceived_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600529
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.InstantMessageModality.InstantMessageReceived
dev_langs:
- CSharp
- JScript
- VB
- other
---

# InstantMessageModality.InstantMessageReceived event

Raised when an instant message is received.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event InstantMessageReceived As EventHandler(Of MessageSentEventArgs)
'Usage
Dim instance As InstantMessageModality
Dim handler As EventHandler(Of MessageSentEventArgs)

AddHandler instance.InstantMessageReceived, handler
```

``` csharp
public event EventHandler<MessageSentEventArgs> InstantMessageReceived
```

## See also

#### Reference

[InstantMessageModality class](instantmessagemodality-class-microsoft-lync-model-conversation_2.md)

[InstantMessageModality members](instantmessagemodality-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

