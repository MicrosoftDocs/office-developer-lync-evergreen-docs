---
title: Modality.BeginTransfer method (ContactEndpoint, TransferOptions, AsyncCallback, Object) (Microsoft.Lync.Model.Conversation)
TOCTitle: BeginTransfer method (ContactEndpoint, TransferOptions, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.BeginTransfer(Microsoft.Lync.Model.ContactEndpoint,Microsoft.Lync.Model.Conversation.AudioVideo.TransferOptions,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.begintransfer(v=office.15)
ms:contentKeyID: 48598400
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Modality.BeginTransfer method (ContactEndpoint, TransferOptions, AsyncCallback, Object)

Transfer an active conversation to a specified remote contact endpoint. You cannot transfer a conversation to another local contact endpoint.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginTransfer ( _
    endpoint As ContactEndpoint, _
    options As TransferOptions, _
    modalityCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Modality
Dim endpoint As ContactEndpoint
Dim options As TransferOptions
Dim modalityCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginTransfer(endpoint, _
    options, modalityCallback, state)
```

``` csharp
public IAsyncResult BeginTransfer(
    ContactEndpoint endpoint,
    TransferOptions options,
    AsyncCallback modalityCallback,
    Object state
)
```

#### Parameters

  - endpoint  
    Type: [Microsoft.Lync.Model.ContactEndpoint](contactendpoint-class-microsoft-lync-model_2.md)  

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

