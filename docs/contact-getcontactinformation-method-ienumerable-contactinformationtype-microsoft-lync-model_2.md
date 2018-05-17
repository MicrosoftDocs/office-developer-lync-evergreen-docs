---
title: Contact.GetContactInformation method (IEnumerable(ContactInformationType)) (Microsoft.Lync.Model)
TOCTitle: GetContactInformation method (IEnumerable(ContactInformationType))
ms:assetid: M:Microsoft.Lync.Model.Contact.GetContactInformation(System.Collections.Generic.IEnumerable{Microsoft.Lync.Model.ContactInformationType})_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.getcontactinformation(v=office.15)
ms:contentKeyID: 48594370
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Contact.GetContactInformation method (IEnumerable\<ContactInformationType\>)

Gets contact information from this contact.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetContactInformation ( _
    contactInformationTypes As IEnumerable(Of ContactInformationType) _
) As IDictionary(Of ContactInformationType, Object)
'Usage
Dim instance As Contact
Dim contactInformationTypes As IEnumerable(Of ContactInformationType)
Dim returnValue As IDictionary(Of ContactInformationType, Object)

returnValue = instance.GetContactInformation(contactInformationTypes)
```

``` csharp
public IDictionary<ContactInformationType, Object> GetContactInformation(
    IEnumerable<ContactInformationType> contactInformationTypes
)
```

#### Parameters

  - contactInformationTypes  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md)\>  

#### Return value

Type: [System.Collections.Generic.IDictionary](http://msdn2.microsoft.com/en-us/library/s4ys34ea)\<[ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[GetContactInformation overload](contact-getcontactinformation-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

