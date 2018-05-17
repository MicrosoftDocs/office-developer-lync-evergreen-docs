---
title: Contact.EndGetOrganizationInformation method  (Microsoft.Lync.Model)
TOCTitle: 'EndGetOrganizationInformation method '
ms:assetid: M:Microsoft.Lync.Model.Contact.EndGetOrganizationInformation(Microsoft.Lync.Model.Group.ContactCollection@,Microsoft.Lync.Model.Group.ContactCollection@,Microsoft.Lync.Model.Group.ContactCollection@,System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.endgetorganizationinformation(v=office.15)
ms:contentKeyID: 48594474
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.EndGetOrganizationInformation
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.EndGetOrganizationInformation method

Gets the Organization Info of this contact.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub EndGetOrganizationInformation ( _
    <OutAttribute> ByRef managers As ContactCollection, _
    <OutAttribute> ByRef peers As ContactCollection, _
    <OutAttribute> ByRef directors As ContactCollection, _
    asyncResult As IAsyncResult _
)
'Usage
Dim instance As Contact
Dim managers As ContactCollection
Dim peers As ContactCollection
Dim directors As ContactCollection
Dim asyncResult As IAsyncResult

instance.EndGetOrganizationInformation(managers, _
    peers, directors, asyncResult)
```

``` csharp
public void EndGetOrganizationInformation(
    out ContactCollection managers,
    out ContactCollection peers,
    out ContactCollection directors,
    IAsyncResult asyncResult
)
```

#### Parameters

  - managers  
    Type: [Microsoft.Lync.Model.Group.ContactCollection](contactcollection-class-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - peers  
    Type: [Microsoft.Lync.Model.Group.ContactCollection](contactcollection-class-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - directors  
    Type: [Microsoft.Lync.Model.Group.ContactCollection](contactcollection-class-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

