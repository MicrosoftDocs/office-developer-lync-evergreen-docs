---
title: GroupCollection.TryGetGroup method  (Microsoft.Lync.Model.Group)
TOCTitle: 'TryGetGroup method '
ms:assetid: M:Microsoft.Lync.Model.Group.GroupCollection.TryGetGroup(System.String,Microsoft.Lync.Model.Group.Group@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.groupcollection.trygetgroup(v=office.15)
ms:contentKeyID: 48589341
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.GroupCollection.TryGetGroup
dev_langs:
- CSharp
- JScript
- VB
- other
---

# GroupCollection.TryGetGroup method

Finds the first group with a given name in a collection.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function TryGetGroup ( _
    groupName As String, _
    <OutAttribute> ByRef value As Group _
) As Boolean
'Usage
Dim instance As GroupCollection
Dim groupName As String
Dim value As Group
Dim returnValue As Boolean

returnValue = instance.TryGetGroup(groupName, _
    value)
```

``` csharp
public bool TryGetGroup(
    string groupName,
    out Group value
)
```

#### Parameters

  - groupName  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - value  
    Type: [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[GroupCollection class](groupcollection-class-microsoft-lync-model-group_2.md)

[GroupCollection members](groupcollection-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

