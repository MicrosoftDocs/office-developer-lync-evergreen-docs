---
title: Modality.BeginTransfer method (Contact, TransferOptions, AsyncCallback, Object) (Microsoft.Lync.Model.Conversation)
TOCTitle: BeginTransfer method (Contact, TransferOptions, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.BeginTransfer(Microsoft.Lync.Model.Contact,Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.begintransfer(v=office.15)
ms:contentKeyID: 48596695
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Modality.BeginTransfer method (Contact, TransferOptions, AsyncCallback, Object)

Transfers an active conversation to a specified remote contact.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginTransfer ( _
    contact As Contact, _
    options As TransferOptions, _
    modalityCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Modality
Dim contact As Contact
Dim options As TransferOptions
Dim modalityCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginTransfer(contact, _
    options, modalityCallback, state)
```

``` csharp
public IAsyncResult BeginTransfer(
    Contact contact,
    TransferOptions options,
    AsyncCallback modalityCallback,
    Object state
)
```

#### Parameters

  - contact  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

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

## Remarks

Available only for the AvModality.

## See also

#### Reference

[Modality class](modality-class-microsoft-lync-model-conversation_2.md)

[Modality members](modality-members-microsoft-lync-model-conversation_2.md)

[BeginTransfer overload](modality-begintransfer-method-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

