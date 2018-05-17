---
title: Utilities.BeginComposeEmail method (IEnumerable(Contact), IEnumerable(DistributionGroup), String, AsyncCallback, Object) (Microsoft.Lync.Model)
TOCTitle: BeginComposeEmail method (IEnumerable(Contact), IEnumerable(DistributionGroup), String, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Utilities.BeginComposeEmail(System.Collections.Generic.IEnumerable{Microsoft.Lync.Model.Contact},System.Collections.Generic.IEnumerable{Microsoft.Lync.Model.Group.DistributionGroup},System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.utilities.begincomposeemail(v=office.15)
ms:contentKeyID: 48593429
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Utilities.BeginComposeEmail method (IEnumerable\<Contact\>, IEnumerable\<DistributionGroup\>, String, AsyncCallback, Object)

Launches a new Outlook message window pre-populated with the email addresses in the specified contact list and subject string passed in the first two arguments of this method.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginComposeEmail ( _
    toContacts As IEnumerable(Of Contact), _
    toDGs As IEnumerable(Of DistributionGroup), _
    subject As String, _
    utilitiesCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Utilities
Dim toContacts As IEnumerable(Of Contact)
Dim toDGs As IEnumerable(Of DistributionGroup)
Dim subject As String
Dim utilitiesCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginComposeEmail(toContacts, _
    toDGs, subject, utilitiesCallback, _
    state)
```

``` csharp
public IAsyncResult BeginComposeEmail(
    IEnumerable<Contact> toContacts,
    IEnumerable<DistributionGroup> toDGs,
    string subject,
    AsyncCallback utilitiesCallback,
    Object state
)
```

#### Parameters

  - toContacts  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[Contact](contact-class-microsoft-lync-model_2.md)\>  

<!-- end list -->

  - toDGs  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[DistributionGroup](distributiongroup-class-microsoft-lync-model-group_2.md)\>  

<!-- end list -->

  - subject  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - utilitiesCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Utilities class](utilities-class-microsoft-lync-model_2.md)

[Utilities members](utilities-members-microsoft-lync-model_2.md)

[BeginComposeEmail overload](utilities-begincomposeemail-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

