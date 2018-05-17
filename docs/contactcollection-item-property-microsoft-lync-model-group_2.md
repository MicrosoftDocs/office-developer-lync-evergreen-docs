---
title: ContactCollection.Item property  (Microsoft.Lync.Model.Group)
TOCTitle: 'Item property '
ms:assetid: P:Microsoft.Lync.Model.Group.ContactCollection.Item(System.Int32)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.contactcollection.item(v=office.15)
ms:contentKeyID: 48594438
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.ContactCollection.Item
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactCollection.Item property

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Default Property Item ( _
    index As Integer _
) As Contact
    Get
    Set
'Usage
Dim instance As ContactCollection
Dim index As Integer
Dim value As Contact

value = instance(index)

instance(index) = value
```

``` csharp
public Contact this[
    int index
] { get; set; }
```

#### Parameters

  - index  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

#### Property value

Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

#### Implements

[IList\<T\>.Item\[Int32\]](http://msdn2.microsoft.com/en-us/library/ewthkb10)  

## See also

#### Reference

[ContactCollection class](contactcollection-class-microsoft-lync-model-group_2.md)

[ContactCollection members](contactcollection-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

