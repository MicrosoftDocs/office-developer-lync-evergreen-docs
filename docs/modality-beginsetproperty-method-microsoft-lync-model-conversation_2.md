---
title: Modality.BeginSetProperty method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginSetProperty method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.BeginSetProperty(Microsoft.Lync.Model.Conversation.ModalityProperty,System.Object,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.beginsetproperty(v=office.15)
ms:contentKeyID: 48599666
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Modality.BeginSetProperty
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Modality.BeginSetProperty method

Sets a property associated with this modality.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSetProperty ( _
    propertyType As ModalityProperty, _
    propertyValue As Object, _
    modalityCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Modality
Dim propertyType As ModalityProperty
Dim propertyValue As Object
Dim modalityCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSetProperty(propertyType, _
    propertyValue, modalityCallback, _
    state)
```

``` csharp
public IAsyncResult BeginSetProperty(
    ModalityProperty propertyType,
    Object propertyValue,
    AsyncCallback modalityCallback,
    Object state
)
```

#### Parameters

  - propertyType  
    Type: [Microsoft.Lync.Model.Conversation.ModalityProperty](modalityproperty-enumeration-microsoft-lync-model-conversation_2.md)  

<!-- end list -->

  - propertyValue  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

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

