---
title: Contact.CanChangeSetting method  (Microsoft.Lync.Model)
TOCTitle: 'CanChangeSetting method '
ms:assetid: M:Microsoft.Lync.Model.Contact.CanChangeSetting(Microsoft.Lync.Model.ContactSetting)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.canchangesetting(v=office.15)
ms:contentKeyID: 48602069
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.CanChangeSetting
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.CanChangeSetting method

Checks if the setting can be set for this contact.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanChangeSetting ( _
    contactSetting As ContactSetting _
) As Boolean
'Usage
Dim instance As Contact
Dim contactSetting As ContactSetting
Dim returnValue As Boolean

returnValue = instance.CanChangeSetting(contactSetting)
```

``` csharp
public bool CanChangeSetting(
    ContactSetting contactSetting
)
```

#### Parameters

  - contactSetting  
    Type: [Microsoft.Lync.Model.ContactSetting](contactsetting-enumeration-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

