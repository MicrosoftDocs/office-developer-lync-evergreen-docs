---
title: ConversationWindow.CanInvoke method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'CanInvoke method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.ConversationWindow.CanInvoke(Microsoft.Lync.Model.Extensibility.ConversationWindowAction)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindow.caninvoke(v=office.15)
ms:contentKeyID: 48593526
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindow.CanInvoke
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindow.CanInvoke method

Returns whether the given action is available

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanInvoke ( _
    action As ConversationWindowAction _
) As Boolean
'Usage
Dim instance As ConversationWindow
Dim action As ConversationWindowAction
Dim returnValue As Boolean

returnValue = instance.CanInvoke(action)
```

``` csharp
public bool CanInvoke(
    ConversationWindowAction action
)
```

#### Parameters

  - action  
    Type: [Microsoft.Lync.Model.Extensibility.ConversationWindowAction](conversationwindowaction-enumeration-microsoft-lync-model-extensibility_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## See also

#### Reference

[ConversationWindow class](conversationwindow-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindow members](conversationwindow-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

