---
title: Conversation.InitialContextReceived event (Microsoft.Lync.Model.Conversation)
TOCTitle: InitialContextReceived event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Conversation.InitialContextReceived_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.initialcontextreceived_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590611
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.InitialContextReceived
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.InitialContextReceived event

Raised to notify of the 3rd party applications of incoming calls .

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event InitialContextReceived As EventHandler(Of InitialContextEventArgs)
'Usage
Dim instance As Conversation
Dim handler As EventHandler(Of InitialContextEventArgs)

AddHandler instance.InitialContextReceived, handler
```

``` csharp
public event EventHandler<InitialContextEventArgs> InitialContextReceived
```

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

