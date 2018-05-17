---
title: Contact.BeginChangeSetting method  (Microsoft.Lync.Model)
TOCTitle: 'BeginChangeSetting method '
ms:assetid: M:Microsoft.Lync.Model.Contact.BeginChangeSetting(Microsoft.Lync.Model.ContactSetting,System.Object,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.beginchangesetting(v=office.15)
ms:contentKeyID: 48594956
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.BeginChangeSetting
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.BeginChangeSetting method

Sets a setting associated with this contact.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginChangeSetting ( _
    contactSettingType As ContactSetting, _
    contactSettingValue As Object, _
    contactCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Contact
Dim contactSettingType As ContactSetting
Dim contactSettingValue As Object
Dim contactCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginChangeSetting(contactSettingType, _
    contactSettingValue, contactCallback, _
    state)
```

``` csharp
public IAsyncResult BeginChangeSetting(
    ContactSetting contactSettingType,
    Object contactSettingValue,
    AsyncCallback contactCallback,
    Object state
)
```

#### Parameters

  - contactSettingType  
    Type: [Microsoft.Lync.Model.ContactSetting](contactsetting-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - contactSettingValue  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

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

