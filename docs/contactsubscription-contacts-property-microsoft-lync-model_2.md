---
title: ContactSubscription.Contacts property  (Microsoft.Lync.Model)
TOCTitle: 'Contacts property '
ms:assetid: P:Microsoft.Lync.Model.ContactSubscription.Contacts_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactsubscription.contacts_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594484
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactSubscription.Contacts
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSubscription.Contacts property

Returns the collection of contacts in a subscription.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Contacts As IList(Of Contact)
    Get
'Usage
Dim instance As ContactSubscription
Dim value As IList(Of Contact)

value = instance.Contacts
```

``` csharp
public IList<Contact> Contacts { get; }
```

#### Property value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[Contact](contact-class-microsoft-lync-model_2.md)\>  

## See also

#### Reference

[ContactSubscription class](contactsubscription-class-microsoft-lync-model_2.md)

[ContactSubscription members](contactsubscription-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

