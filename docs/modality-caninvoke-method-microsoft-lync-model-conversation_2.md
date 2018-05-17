---
title: Modality.CanInvoke method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'CanInvoke method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.CanInvoke(Microsoft.Lync.Model.Conversation.ModalityAction)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.caninvoke(v=office.15)
ms:contentKeyID: 48591724
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Modality.CanInvoke
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Modality.CanInvoke method

Returns a flag indicating whether a specific action is available.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanInvoke ( _
    action As ModalityAction _
) As Boolean
'Usage
Dim instance As Modality
Dim action As ModalityAction
Dim returnValue As Boolean

returnValue = instance.CanInvoke(action)
```

``` csharp
public bool CanInvoke(
    ModalityAction action
)
```

#### Parameters

  - action  
    Type: [Microsoft.Lync.Model.Conversation.ModalityAction](modalityaction-enumeration-microsoft-lync-model-conversation_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## See also

#### Reference

[Modality class](modality-class-microsoft-lync-model-conversation_2.md)

[Modality members](modality-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

