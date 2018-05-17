---
title: GroupCollection.Item property  (Microsoft.Lync.Model.Group)
TOCTitle: 'Item property '
ms:assetid: P:Microsoft.Lync.Model.Group.GroupCollection.Item(System.Int32)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.groupcollection.item(v=office.15)
ms:contentKeyID: 48590495
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.GroupCollection.Item
dev_langs:
- CSharp
- JScript
- VB
- other
---

# GroupCollection.Item property

Returns an item at a given index in the collection.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Default Property Item ( _
    _index As Integer _
) As Group
    Get
    Set
'Usage
Dim instance As GroupCollection
Dim _index As Integer
Dim value As Group

value = instance(_index)

instance(_index) = value
```

``` csharp
public Group this[
    int _index
] { get; set; }
```

#### Parameters

  - \_index  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

#### Property value

Type: [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md)  

#### Implements

[IList\<T\>.Item\[Int32\]](http://msdn2.microsoft.com/en-us/library/ewthkb10)  

## See also

#### Reference

[GroupCollection class](groupcollection-class-microsoft-lync-model-group_2.md)

[GroupCollection members](groupcollection-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

