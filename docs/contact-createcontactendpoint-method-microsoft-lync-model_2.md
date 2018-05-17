---
title: Contact.CreateContactEndpoint method  (Microsoft.Lync.Model)
TOCTitle: 'CreateContactEndpoint method '
ms:assetid: M:Microsoft.Lync.Model.Contact.CreateContactEndpoint(System.String)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.createcontactendpoint(v=office.15)
ms:contentKeyID: 48590519
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.CreateContactEndpoint
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.CreateContactEndpoint method

Creates a collaboration endpoint object from a telephone number.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CreateContactEndpoint ( _
    telephoneUri As String _
) As ContactEndpoint
'Usage
Dim instance As Contact
Dim telephoneUri As String
Dim returnValue As ContactEndpoint

returnValue = instance.CreateContactEndpoint(telephoneUri)
```

``` csharp
public ContactEndpoint CreateContactEndpoint(
    string telephoneUri
)
```

#### Parameters

  - telephoneUri  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

#### Return value

Type: [Microsoft.Lync.Model.ContactEndpoint](contactendpoint-class-microsoft-lync-model_2.md)  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

