---
title: ContactCollection.TryGetContact method  (Microsoft.Lync.Model.Group)
TOCTitle: 'TryGetContact method '
ms:assetid: M:Microsoft.Lync.Model.Group.ContactCollection.TryGetContact(System.String,Microsoft.Lync.Model.Contact@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.contactcollection.trygetcontact(v=office.15)
ms:contentKeyID: 48594530
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.ContactCollection.TryGetContact
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactCollection.TryGetContact method

Tries to find the first contact with the given Uri.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function TryGetContact ( _
    uri As String, _
    <OutAttribute> ByRef value As Contact _
) As Boolean
'Usage
Dim instance As ContactCollection
Dim uri As String
Dim value As Contact
Dim returnValue As Boolean

returnValue = instance.TryGetContact(uri, _
    value)
```

``` csharp
public bool TryGetContact(
    string uri,
    out Contact value
)
```

#### Parameters

  - uri  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - value  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[ContactCollection class](contactcollection-class-microsoft-lync-model-group_2.md)

[ContactCollection members](contactcollection-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

