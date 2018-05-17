---
title: Contact.BeginGetOrganizationInformation method  (Microsoft.Lync.Model)
TOCTitle: 'BeginGetOrganizationInformation method '
ms:assetid: M:Microsoft.Lync.Model.Contact.BeginGetOrganizationInformation(Microsoft.Lync.Model.OrganizationStructureTypes,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.begingetorganizationinformation(v=office.15)
ms:contentKeyID: 48588646
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.BeginGetOrganizationInformation
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.BeginGetOrganizationInformation method

Gets the Organization Info of this contact.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginGetOrganizationInformation ( _
    orgInfoTypes As OrganizationStructureTypes, _
    contactCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Contact
Dim orgInfoTypes As OrganizationStructureTypes
Dim contactCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginGetOrganizationInformation(orgInfoTypes, _
    contactCallback, state)
```

``` csharp
public IAsyncResult BeginGetOrganizationInformation(
    OrganizationStructureTypes orgInfoTypes,
    AsyncCallback contactCallback,
    Object state
)
```

#### Parameters

  - orgInfoTypes  
    Type: [Microsoft.Lync.Model.OrganizationStructureTypes](organizationstructuretypes-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - contactCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

