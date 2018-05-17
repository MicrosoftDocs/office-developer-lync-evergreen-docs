---
title: GroupCollection.GetGroupsByType method  (Microsoft.Lync.Model.Group)
TOCTitle: 'GetGroupsByType method '
ms:assetid: M:Microsoft.Lync.Model.Group.GroupCollection.GetGroupsByType(Microsoft.Lync.Model.Group.GroupType)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.groupcollection.getgroupsbytype(v=office.15)
ms:contentKeyID: 48593948
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.GroupCollection.GetGroupsByType
dev_langs:
- CSharp
- JScript
- VB
- other
---

# GroupCollection.GetGroupsByType method

Gets a collection of groups of a given group type.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetGroupsByType ( _
    groupType As GroupType _
) As GroupCollection
'Usage
Dim instance As GroupCollection
Dim groupType As GroupType
Dim returnValue As GroupCollection

returnValue = instance.GetGroupsByType(groupType)
```

``` csharp
public GroupCollection GetGroupsByType(
    GroupType groupType
)
```

#### Parameters

  - groupType  
    Type: [Microsoft.Lync.Model.Group.GroupType](grouptype-enumeration-microsoft-lync-model-group_2.md)  

#### Return value

Type: [Microsoft.Lync.Model.Group.GroupCollection](groupcollection-class-microsoft-lync-model-group_2.md)  
IGroupCollection  

## See also

#### Reference

[GroupCollection class](groupcollection-class-microsoft-lync-model-group_2.md)

[GroupCollection members](groupcollection-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

