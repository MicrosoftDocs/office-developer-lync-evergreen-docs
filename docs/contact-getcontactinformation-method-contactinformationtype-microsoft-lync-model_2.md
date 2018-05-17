---
title: Contact.GetContactInformation method (ContactInformationType) (Microsoft.Lync.Model)
TOCTitle: GetContactInformation method (ContactInformationType)
ms:assetid: M:Microsoft.Lync.Model.Contact.GetContactInformation(Microsoft.Lync.Model.ContactInformationType)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.getcontactinformation(v=office.15)
ms:contentKeyID: 48591752
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Contact.GetContactInformation method (ContactInformationType)

Gets a single contact information from this contact.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetContactInformation ( _
    contactInformationType As ContactInformationType _
) As Object
'Usage
Dim instance As Contact
Dim contactInformationType As ContactInformationType
Dim returnValue As Object

returnValue = instance.GetContactInformation(contactInformationType)
```

``` csharp
public Object GetContactInformation(
    ContactInformationType contactInformationType
)
```

#### Parameters

  - contactInformationType  
    Type: [Microsoft.Lync.Model.ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
System.Object  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[GetContactInformation overload](contact-getcontactinformation-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

