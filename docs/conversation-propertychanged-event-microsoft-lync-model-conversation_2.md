---
title: Conversation.PropertyChanged event (Microsoft.Lync.Model.Conversation)
TOCTitle: PropertyChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Conversation.PropertyChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.propertychanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596727
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.PropertyChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.PropertyChanged event

Raised when a property value changes

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event PropertyChanged As EventHandler(Of ConversationPropertyChangedEventArgs)
'Usage
Dim instance As Conversation
Dim handler As EventHandler(Of ConversationPropertyChangedEventArgs)

AddHandler instance.PropertyChanged, handler
```

``` csharp
public event EventHandler<ConversationPropertyChangedEventArgs> PropertyChanged
```

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

