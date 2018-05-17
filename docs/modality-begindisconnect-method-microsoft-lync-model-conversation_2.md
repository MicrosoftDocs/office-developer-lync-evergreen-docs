---
title: Modality.BeginDisconnect method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginDisconnect method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.BeginDisconnect(Microsoft.Lync.Model.Conversation.ModalityDisconnectReason,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.begindisconnect(v=office.15)
ms:contentKeyID: 48593513
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Modality.BeginDisconnect
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Modality.BeginDisconnect method

Disconnects from the modality.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginDisconnect ( _
    reason As ModalityDisconnectReason, _
    modalityCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Modality
Dim reason As ModalityDisconnectReason
Dim modalityCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginDisconnect(reason, _
    modalityCallback, state)
```

``` csharp
public IAsyncResult BeginDisconnect(
    ModalityDisconnectReason reason,
    AsyncCallback modalityCallback,
    Object state
)
```

#### Parameters

  - reason  
    Type: [Microsoft.Lync.Model.Conversation.ModalityDisconnectReason](modalitydisconnectreason-enumeration-microsoft-lync-model-conversation_2.md)  

<!-- end list -->

  - modalityCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Modality class](modality-class-microsoft-lync-model-conversation_2.md)

[Modality members](modality-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

