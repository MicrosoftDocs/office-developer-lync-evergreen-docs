---
title: Conversation.ContextDataReceived event (Microsoft.Lync.Model.Conversation)
TOCTitle: ContextDataReceived event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Conversation.ContextDataReceived_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.contextdatareceived_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595789
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.ContextDataReceived
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.ContextDataReceived event

Raised to notify of the 3rd party applications of incoming info.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ContextDataReceived As EventHandler(Of ContextEventArgs)
'Usage
Dim instance As Conversation
Dim handler As EventHandler(Of ContextEventArgs)

AddHandler instance.ContextDataReceived, handler
```

``` csharp
public event EventHandler<ContextEventArgs> ContextDataReceived
```

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

