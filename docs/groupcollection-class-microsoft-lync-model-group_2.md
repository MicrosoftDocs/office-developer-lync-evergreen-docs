---
title: GroupCollection class (Microsoft.Lync.Model.Group)
TOCTitle: GroupCollection class
ms:assetid: T:Microsoft.Lync.Model.Group.GroupCollection_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.groupcollection_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600357
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.GroupCollection
dev_langs:
- CSharp
- JScript
- VB
- other
---

# GroupCollection class

Represents the collection of all groups in the signed in user's contact list.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWLite**  
        Microsoft.Lync.Model.Group.GroupCollection  

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class GroupCollection _
    Inherits UCWLite _
    Implements IList(Of Group), ICollection(Of Group),  _
    IEnumerable(Of Group), IEnumerable
'Usage
Dim instance As GroupCollection
```

``` csharp
public class GroupCollection : UCWLite, 
    IList<Group>, ICollection<Group>, IEnumerable<Group>, 
    IEnumerable
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[GroupCollection members](groupcollection-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

