---
title: Group class (Microsoft.Lync.Model.Group)
TOCTitle: Group class
ms:assetid: T:Microsoft.Lync.Model.Group.Group_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.group_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48588593
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.Group
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Group class

Represents a group of contacts.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWFull**  
        [Microsoft.Lync.Model.Group.ContactCollection](contactcollection-class-microsoft-lync-model-group_2.md)  
          Microsoft.Lync.Model.Group.Group  
            [Microsoft.Lync.Model.Group.CustomGroup](customgroup-class-microsoft-lync-model-group_2.md)  
            [Microsoft.Lync.Model.Group.DistributionGroup](distributiongroup-class-microsoft-lync-model-group_2.md)  
            [Microsoft.Lync.Model.Group.FavoriteContacts](favoritecontacts-class-microsoft-lync-model-group_2.md)  
            [Microsoft.Lync.Model.Group.FrequentContacts](frequentcontacts-class-microsoft-lync-model-group_2.md)  

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public MustInherit Class Group _
    Inherits ContactCollection
'Usage
Dim instance As Group
```

``` csharp
public abstract class Group : ContactCollection
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[Group members](group-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

