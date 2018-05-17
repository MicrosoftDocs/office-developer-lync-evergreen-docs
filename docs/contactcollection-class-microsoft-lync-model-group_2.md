---
title: ContactCollection class (Microsoft.Lync.Model.Group)
TOCTitle: ContactCollection class
ms:assetid: T:Microsoft.Lync.Model.Group.ContactCollection_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.contactcollection_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591201
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.ContactCollection
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactCollection class

Represents a collection of contacts that can be individually accessed by index.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWFull**  
        Microsoft.Lync.Model.Group.ContactCollection  
          [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md)  

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class ContactCollection _
    Inherits UCWFull _
    Implements IList(Of Contact), ICollection(Of Contact),  _
    IEnumerable(Of Contact), IEnumerable
'Usage
Dim instance As ContactCollection
```

``` csharp
public class ContactCollection : UCWFull, 
    IList<Contact>, ICollection<Contact>, IEnumerable<Contact>, 
    IEnumerable
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactCollection members](contactcollection-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

