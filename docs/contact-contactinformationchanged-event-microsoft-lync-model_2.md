---
title: Contact.ContactInformationChanged event (Microsoft.Lync.Model)
TOCTitle: ContactInformationChanged event
ms:assetid: E:Microsoft.Lync.Model.Contact.ContactInformationChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.contactinformationchanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594983
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.ContactInformationChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.ContactInformationChanged event

Occurs when one or more pieces of contact information are changed.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ContactInformationChanged As EventHandler(Of ContactInformationChangedEventArgs)
'Usage
Dim instance As Contact
Dim handler As EventHandler(Of ContactInformationChangedEventArgs)

AddHandler instance.ContactInformationChanged, handler
```

``` csharp
public event EventHandler<ContactInformationChangedEventArgs> ContactInformationChanged
```

## Remarks

Application logic must subscribe to contact information publication before the ContactInformationChanged event can be received. Call the CreateSubscription method on the ContactManager object and then add the Contact to be subscribed and the ContactInformationTypes that you are interested in. Finally, call the Subscribe method on the ContactSubscription object.

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

