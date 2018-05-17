---
title: Modality.BeginConsultativeTransfer method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginConsultativeTransfer method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.BeginConsultativeTransfer(Microsoft.Lync.Model.Conversation.Conversation,Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.beginconsultativetransfer(v=office.15)
ms:contentKeyID: 48589338
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Modality.BeginConsultativeTransfer
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Modality.BeginConsultativeTransfer method

Transfers a connected modality to an existing conversation.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginConsultativeTransfer ( _
    conversation As Conversation, _
    options As TransferOptions, _
    modalityCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Modality
Dim conversation As Conversation
Dim options As TransferOptions
Dim modalityCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginConsultativeTransfer(conversation, _
    options, modalityCallback, state)
```

``` csharp
public IAsyncResult BeginConsultativeTransfer(
    Conversation conversation,
    TransferOptions options,
    AsyncCallback modalityCallback,
    Object state
)
```

#### Parameters

  - conversation  
    Type: [Microsoft.Lync.Model.Conversation.Conversation](conversation-class-microsoft-lync-model-conversation_2.md)  

<!-- end list -->

  - options  
    Type: [Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions](transferoptions-enumeration-microsoft-lync-model-conversation-audiovideo_2.md)  

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

