---
title: ContactSubscription.Subscribe method  (Microsoft.Lync.Model)
TOCTitle: 'Subscribe method '
ms:assetid: M:Microsoft.Lync.Model.ContactSubscription.Subscribe(Microsoft.Lync.Model.ContactSubscriptionRefreshRate,System.Collections.Generic.IEnumerable{Microsoft.Lync.Model.ContactInformationType})_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactsubscription.subscribe(v=office.15)
ms:contentKeyID: 48599443
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactSubscription.Subscribe
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSubscription.Subscribe method

if a contact is removed from the subscription, the subscription to this contact can only be removed when Unsubscribe or UpdateSubscription is called.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub Subscribe ( _
    subscriptionFreshness As ContactSubscriptionRefreshRate, _
    contactInformationTypes As IEnumerable(Of ContactInformationType) _
)
'Usage
Dim instance As ContactSubscription
Dim subscriptionFreshness As ContactSubscriptionRefreshRate
Dim contactInformationTypes As IEnumerable(Of ContactInformationType)

instance.Subscribe(subscriptionFreshness, _
    contactInformationTypes)
```

``` csharp
public void Subscribe(
    ContactSubscriptionRefreshRate subscriptionFreshness,
    IEnumerable<ContactInformationType> contactInformationTypes
)
```

#### Parameters

  - subscriptionFreshness  
    Type: [Microsoft.Lync.Model.ContactSubscriptionRefreshRate](contactsubscriptionrefreshrate-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - contactInformationTypes  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md)\>  

## See also

#### Reference

[ContactSubscription class](contactsubscription-class-microsoft-lync-model_2.md)

[ContactSubscription members](contactsubscription-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

