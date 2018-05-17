---
title: Modality.BeginForward method (Contact, AsyncCallback, Object) (Microsoft.Lync.Model.Conversation)
TOCTitle: BeginForward method (Contact, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.BeginForward(Microsoft.Lync.Model.Contact,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.beginforward(v=office.15)
ms:contentKeyID: 48602062
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Modality.BeginForward method (Contact, AsyncCallback, Object)

Forwards an active conversation (in ringing state) to a specified remote contact endpoint. You cannot forward conversations between the local contacts endpoints.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginForward ( _
    contact As Contact, _
    modalityCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Modality
Dim contact As Contact
Dim modalityCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginForward(contact, _
    modalityCallback, state)
```

``` csharp
public IAsyncResult BeginForward(
    Contact contact,
    AsyncCallback modalityCallback,
    Object state
)
```

#### Parameters

  - contact  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

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

[BeginForward overload](modality-beginforward-method-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

