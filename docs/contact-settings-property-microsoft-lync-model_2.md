---
title: Contact.Settings property  (Microsoft.Lync.Model)
TOCTitle: 'Settings property '
ms:assetid: P:Microsoft.Lync.Model.Contact.Settings_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.settings_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599099
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.Settings
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.Settings property

Gets a collection of contact settings.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Settings As IDictionary(Of ContactSetting, Object)
    Get
'Usage
Dim instance As Contact
Dim value As IDictionary(Of ContactSetting, Object)

value = instance.Settings
```

``` csharp
public IDictionary<ContactSetting, Object> Settings { get; }
```

#### Property value

Type: [System.Collections.Generic.IDictionary](http://msdn2.microsoft.com/en-us/library/s4ys34ea)\<[ContactSetting](contactsetting-enumeration-microsoft-lync-model_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

