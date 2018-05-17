---
title: ApplicationSharingModality.BeginAcceptControlRequest method  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'BeginAcceptControlRequest method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.BeginAcceptControlRequest(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingmodality.beginacceptcontrolrequest(v=office.15)
ms:contentKeyID: 48594462
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.BeginAcceptControlRequest
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ApplicationSharingModality.BeginAcceptControlRequest method

Accepts a pending control request.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginAcceptControlRequest ( _
    modalityCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ApplicationSharingModality
Dim modalityCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginAcceptControlRequest(modalityCallback, _
    state)
```

``` csharp
public IAsyncResult BeginAcceptControlRequest(
    AsyncCallback modalityCallback,
    Object state
)
```

#### Parameters

  - modalityCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[ApplicationSharingModality class](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ApplicationSharingModality members](applicationsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

