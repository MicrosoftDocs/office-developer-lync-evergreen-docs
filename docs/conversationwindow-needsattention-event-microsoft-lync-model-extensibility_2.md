---
title: ConversationWindow.NeedsAttention event (Microsoft.Lync.Model.Extensibility)
TOCTitle: NeedsAttention event
ms:assetid: E:Microsoft.Lync.Model.Extensibility.ConversationWindow.NeedsAttention_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindow.needsattention_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597729
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindow.NeedsAttention
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindow.NeedsAttention event

Raised when the UI Window needs attention.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event NeedsAttention As EventHandler(Of ConversationWindowNeedsAttentionEventArgs)
'Usage
Dim instance As ConversationWindow
Dim handler As EventHandler(Of ConversationWindowNeedsAttentionEventArgs)

AddHandler instance.NeedsAttention, handler
```

``` csharp
public event EventHandler<ConversationWindowNeedsAttentionEventArgs> NeedsAttention
```

## See also

#### Reference

[ConversationWindow class](conversationwindow-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindow members](conversationwindow-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

