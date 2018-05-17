---
title: DistributionGroup.EndGetAllMembers method  (Microsoft.Lync.Model.Group)
TOCTitle: 'EndGetAllMembers method '
ms:assetid: M:Microsoft.Lync.Model.Group.DistributionGroup.EndGetAllMembers(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.distributiongroup.endgetallmembers(v=office.15)
ms:contentKeyID: 48593491
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.DistributionGroup.EndGetAllMembers
dev_langs:
- CSharp
- JScript
- VB
- other
---

# DistributionGroup.EndGetAllMembers method

Gets all group members.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndGetAllMembers ( _
    asyncResult As IAsyncResult _
) As ContactCollection
'Usage
Dim instance As DistributionGroup
Dim asyncResult As IAsyncResult
Dim returnValue As ContactCollection

returnValue = instance.EndGetAllMembers(asyncResult)
```

``` csharp
public ContactCollection EndGetAllMembers(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Group.ContactCollection](contactcollection-class-microsoft-lync-model-group_2.md)  

## See also

#### Reference

[DistributionGroup class](distributiongroup-class-microsoft-lync-model-group_2.md)

[DistributionGroup members](distributiongroup-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

