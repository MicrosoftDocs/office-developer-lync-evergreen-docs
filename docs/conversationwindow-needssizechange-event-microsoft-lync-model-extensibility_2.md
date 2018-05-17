---
title: ConversationWindow.NeedsSizeChange event (Microsoft.Lync.Model.Extensibility)
TOCTitle: NeedsSizeChange event
ms:assetid: E:Microsoft.Lync.Model.Extensibility.ConversationWindow.NeedsSizeChange_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindow.needssizechange_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599574
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindow.NeedsSizeChange
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindow.NeedsSizeChange event

Raised when the UI Window size changes.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event NeedsSizeChange As EventHandler(Of ConversationWindowNeedsSizeChangeEventArgs)
'Usage
Dim instance As ConversationWindow
Dim handler As EventHandler(Of ConversationWindowNeedsSizeChangeEventArgs)

AddHandler instance.NeedsSizeChange, handler
```

``` csharp
public event EventHandler<ConversationWindowNeedsSizeChangeEventArgs> NeedsSizeChange
```

## See also

#### Reference

[ConversationWindow class](conversationwindow-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindow members](conversationwindow-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

