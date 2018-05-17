---
title: ContactManager.GetContactByUri method  (Microsoft.Lync.Model)
TOCTitle: 'GetContactByUri method '
ms:assetid: M:Microsoft.Lync.Model.ContactManager.GetContactByUri(System.String)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.getcontactbyuri(v=office.15)
ms:contentKeyID: 48592727
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactManager.GetContactByUri
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactManager.GetContactByUri method

Finds or creates a new contact using the contact URI.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetContactByUri ( _
    contactUri As String _
) As Contact
'Usage
Dim instance As ContactManager
Dim contactUri As String
Dim returnValue As Contact

returnValue = instance.GetContactByUri(contactUri)
```

``` csharp
public Contact GetContactByUri(
    string contactUri
)
```

#### Parameters

  - contactUri  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

#### Return value

Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  
Microsoft.Lync.Model.Contact  

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

