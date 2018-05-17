---
title: ContactEndpoint.CanStart method  (Microsoft.Lync.Model)
TOCTitle: 'CanStart method '
ms:assetid: M:Microsoft.Lync.Model.ContactEndpoint.CanStart(Microsoft.Lync.Model.Conversation.ModalityTypes)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactendpoint.canstart(v=office.15)
ms:contentKeyID: 48597529
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactEndpoint.CanStart
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactEndpoint.CanStart method

Checks if this endpoint can start a given mode of communication (modality

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanStart ( _
    modalityTypes As ModalityTypes _
) As Boolean
'Usage
Dim instance As ContactEndpoint
Dim modalityTypes As ModalityTypes
Dim returnValue As Boolean

returnValue = instance.CanStart(modalityTypes)
```

``` csharp
public bool CanStart(
    ModalityTypes modalityTypes
)
```

#### Parameters

  - modalityTypes  
    Type: [Microsoft.Lync.Model.Conversation.ModalityTypes](modalitytypes-enumeration-microsoft-lync-model-conversation_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[ContactEndpoint class](contactendpoint-class-microsoft-lync-model_2.md)

[ContactEndpoint members](contactendpoint-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

