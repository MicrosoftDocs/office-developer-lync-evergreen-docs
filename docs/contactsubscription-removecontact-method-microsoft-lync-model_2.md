---
title: ContactSubscription.RemoveContact method  (Microsoft.Lync.Model)
TOCTitle: 'RemoveContact method '
ms:assetid: M:Microsoft.Lync.Model.ContactSubscription.RemoveContact(Microsoft.Lync.Model.Contact)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactsubscription.removecontact(v=office.15)
ms:contentKeyID: 48600909
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactSubscription.RemoveContact
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSubscription.RemoveContact method

Removes a contact from a subscription.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub RemoveContact ( _
    contact As Contact _
)
'Usage
Dim instance As ContactSubscription
Dim contact As Contact

instance.RemoveContact(contact)
```

``` csharp
public void RemoveContact(
    Contact contact
)
```

#### Parameters

  - contact  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

## Remarks

It is not necessary to call ContactSubscription.Subscribe after removing a contact from a subscription.

## See also

#### Reference

[ContactSubscription class](contactsubscription-class-microsoft-lync-model_2.md)

[ContactSubscription members](contactsubscription-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

