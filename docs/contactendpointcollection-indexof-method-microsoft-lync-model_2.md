---
title: ContactEndpointCollection.IndexOf method  (Microsoft.Lync.Model)
TOCTitle: 'IndexOf method '
ms:assetid: M:Microsoft.Lync.Model.ContactEndpointCollection.IndexOf(Microsoft.Lync.Model.ContactEndpoint)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactendpointcollection.indexof(v=office.15)
ms:contentKeyID: 48595811
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactEndpointCollection.IndexOf
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactEndpointCollection.IndexOf method

Return the index of the contact endpoint in the collection.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function IndexOf ( _
    contactEndpoint As ContactEndpoint _
) As Integer
'Usage
Dim instance As ContactEndpointCollection
Dim contactEndpoint As ContactEndpoint
Dim returnValue As Integer

returnValue = instance.IndexOf(contactEndpoint)
```

``` csharp
public int IndexOf(
    ContactEndpoint contactEndpoint
)
```

#### Parameters

  - contactEndpoint  
    Type: [Microsoft.Lync.Model.ContactEndpoint](contactendpoint-class-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  
int  

#### Implements

[IList\<T\>.IndexOf(T)](http://msdn2.microsoft.com/en-us/library/3w0148af)  

## See also

#### Reference

[ContactEndpointCollection class](contactendpointcollection-class-microsoft-lync-model_2.md)

[ContactEndpointCollection members](contactendpointcollection-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

