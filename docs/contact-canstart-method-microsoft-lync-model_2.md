---
title: Contact.CanStart method  (Microsoft.Lync.Model)
TOCTitle: 'CanStart method '
ms:assetid: M:Microsoft.Lync.Model.Contact.CanStart(Microsoft.Lync.Model.Conversation.ModalityTypes)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.canstart(v=office.15)
ms:contentKeyID: 48602029
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.CanStart
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.CanStart method

Checks if this contact can start a given mode of communication (modality

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanStart ( _
    modalityTypes As ModalityTypes _
) As Boolean
'Usage
Dim instance As Contact
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

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

