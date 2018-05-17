---
title: ContactEndpointCollection.Item property  (Microsoft.Lync.Model)
TOCTitle: 'Item property '
ms:assetid: P:Microsoft.Lync.Model.ContactEndpointCollection.Item(System.Int32)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactendpointcollection.item(v=office.15)
ms:contentKeyID: 48601742
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactEndpointCollection.Item
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactEndpointCollection.Item property

Given an index, returns an item in the collection.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Default Property Item ( _
    _index As Integer _
) As ContactEndpoint
    Get
    Set
'Usage
Dim instance As ContactEndpointCollection
Dim _index As Integer
Dim value As ContactEndpoint

value = instance(_index)

instance(_index) = value
```

``` csharp
public ContactEndpoint this[
    int _index
] { get; set; }
```

#### Parameters

  - \_index  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

#### Property value

Type: [Microsoft.Lync.Model.ContactEndpoint](contactendpoint-class-microsoft-lync-model_2.md)  

#### Implements

[IList\<T\>.Item\[Int32\]](http://msdn2.microsoft.com/en-us/library/ewthkb10)  

## See also

#### Reference

[ContactEndpointCollection class](contactendpointcollection-class-microsoft-lync-model_2.md)

[ContactEndpointCollection members](contactendpointcollection-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

