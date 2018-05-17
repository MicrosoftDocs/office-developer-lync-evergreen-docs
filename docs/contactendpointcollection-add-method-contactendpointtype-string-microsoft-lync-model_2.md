---
title: ContactEndpointCollection.Add method (ContactEndpointType, String) (Microsoft.Lync.Model)
TOCTitle: Add method (ContactEndpointType, String)
ms:assetid: M:Microsoft.Lync.Model.ContactEndpointCollection.Add(Microsoft.Lync.Model.ContactEndpointType,System.String)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactendpointcollection.add(v=office.15)
ms:contentKeyID: 48595347
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# ContactEndpointCollection.Add method (ContactEndpointType, String)

Adds a contact endpoint Uri by endpoint type to the list.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub Add ( _
    endpointType As ContactEndpointType, _
    endpointUri As String _
)
'Usage
Dim instance As ContactEndpointCollection
Dim endpointType As ContactEndpointType
Dim endpointUri As String

instance.Add(endpointType, endpointUri)
```

``` csharp
public void Add(
    ContactEndpointType endpointType,
    string endpointUri
)
```

#### Parameters

  - endpointType  
    Type: [Microsoft.Lync.Model.ContactEndpointType](contactendpointtype-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - endpointUri  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

## See also

#### Reference

[ContactEndpointCollection class](contactendpointcollection-class-microsoft-lync-model_2.md)

[ContactEndpointCollection members](contactendpointcollection-members-microsoft-lync-model_2.md)

[Add overload](contactendpointcollection-add-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

