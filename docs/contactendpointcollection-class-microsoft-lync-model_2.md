---
title: ContactEndpointCollection class (Microsoft.Lync.Model)
TOCTitle: ContactEndpointCollection class
ms:assetid: T:Microsoft.Lync.Model.ContactEndpointCollection_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactendpointcollection_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600907
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactEndpointCollection
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactEndpointCollection class

Represents a collection of endpoint identifiers available to a signed in user.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWLite**  
        Microsoft.Lync.Model.ContactEndpointCollection  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class ContactEndpointCollection _
    Inherits UCWLite _
    Implements IList(Of ContactEndpoint), ICollection(Of ContactEndpoint),  _
    IEnumerable(Of ContactEndpoint), IEnumerable
'Usage
Dim instance As ContactEndpointCollection
```

``` csharp
public class ContactEndpointCollection : UCWLite, 
    IList<ContactEndpoint>, ICollection<ContactEndpoint>, IEnumerable<ContactEndpoint>, 
    IEnumerable
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactEndpointCollection members](contactendpointcollection-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

