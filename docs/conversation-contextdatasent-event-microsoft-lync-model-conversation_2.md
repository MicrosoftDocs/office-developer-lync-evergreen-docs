---
title: Conversation.ContextDataSent event (Microsoft.Lync.Model.Conversation)
TOCTitle: ContextDataSent event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Conversation.ContextDataSent_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.contextdatasent_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600576
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.ContextDataSent
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.ContextDataSent event

Raised to notify of the 3rd party applications of outgoing info.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ContextDataSent As EventHandler(Of ContextEventArgs)
'Usage
Dim instance As Conversation
Dim handler As EventHandler(Of ContextEventArgs)

AddHandler instance.ContextDataSent, handler
```

``` csharp
public event EventHandler<ContextEventArgs> ContextDataSent
```

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

