---
title: InstantMessageModality.IsTypingChanged event (Microsoft.Lync.Model.Conversation)
TOCTitle: IsTypingChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.InstantMessageModality.IsTypingChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.instantmessagemodality.istypingchanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601832
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.InstantMessageModality.IsTypingChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# InstantMessageModality.IsTypingChanged event

Raised when the istyping state changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event IsTypingChanged As EventHandler(Of IsTypingChangedEventArgs)
'Usage
Dim instance As InstantMessageModality
Dim handler As EventHandler(Of IsTypingChangedEventArgs)

AddHandler instance.IsTypingChanged, handler
```

``` csharp
public event EventHandler<IsTypingChangedEventArgs> IsTypingChanged
```

## See also

#### Reference

[InstantMessageModality class](instantmessagemodality-class-microsoft-lync-model-conversation_2.md)

[InstantMessageModality members](instantmessagemodality-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

