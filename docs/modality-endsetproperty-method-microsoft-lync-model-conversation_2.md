---
title: Modality.EndSetProperty method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'EndSetProperty method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.EndSetProperty(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.endsetproperty(v=office.15)
ms:contentKeyID: 48601543
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Modality.EndSetProperty
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Modality.EndSetProperty method

Sets a property associated with this modality.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndSetProperty ( _
    asyncResult As IAsyncResult _
) As ModalityProperty
'Usage
Dim instance As Modality
Dim asyncResult As IAsyncResult
Dim returnValue As ModalityProperty

returnValue = instance.EndSetProperty(asyncResult)
```

``` csharp
public ModalityProperty EndSetProperty(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Conversation.ModalityProperty](modalityproperty-enumeration-microsoft-lync-model-conversation_2.md)  

## See also

#### Reference

[Modality class](modality-class-microsoft-lync-model-conversation_2.md)

[Modality members](modality-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

