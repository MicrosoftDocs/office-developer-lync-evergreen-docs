---
title: ConversationWindow.StateChanged event (Microsoft.Lync.Model.Extensibility)
TOCTitle: StateChanged event
ms:assetid: E:Microsoft.Lync.Model.Extensibility.ConversationWindow.StateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindow.statechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48593451
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindow.StateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindow.StateChanged event

Raised when the conversation window state changes.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event StateChanged As EventHandler(Of ConversationWindowStateChangedEventArgs)
'Usage
Dim instance As ConversationWindow
Dim handler As EventHandler(Of ConversationWindowStateChangedEventArgs)

AddHandler instance.StateChanged, handler
```

``` csharp
public event EventHandler<ConversationWindowStateChangedEventArgs> StateChanged
```

## See also

#### Reference

[ConversationWindow class](conversationwindow-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindow members](conversationwindow-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

