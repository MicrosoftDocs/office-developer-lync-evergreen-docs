---
title: ContactSubscription class (Microsoft.Lync.Model)
TOCTitle: ContactSubscription class
ms:assetid: T:Microsoft.Lync.Model.ContactSubscription_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactsubscription_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592221
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactSubscription
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSubscription class

Specifies the type of contact information to be to be subscribed on a collection of contacts set in the subscription.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWLite**  
        Microsoft.Lync.Model.ContactSubscription  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class ContactSubscription _
    Inherits UCWLite
'Usage
Dim instance As ContactSubscription
```

``` csharp
public class ContactSubscription : UCWLite
```

## Remarks

You must cache a ContactSubscription that you create to maintain subscriptions to contacts you get using the search feature, call into GetContactByUri, or other methods that return Contact instances that are not in the Lync client contact list. You continue to receive contact information updates for the contacts in the cached ContactSubscription until you either un-subscribe to the contacts or destroy the ContactSubscription. The ContactSubscription is cached as a class member.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactSubscription members](contactsubscription-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

