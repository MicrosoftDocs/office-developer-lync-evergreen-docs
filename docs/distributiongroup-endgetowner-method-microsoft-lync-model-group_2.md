---
title: DistributionGroup.EndGetOwner method  (Microsoft.Lync.Model.Group)
TOCTitle: 'EndGetOwner method '
ms:assetid: M:Microsoft.Lync.Model.Group.DistributionGroup.EndGetOwner(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.distributiongroup.endgetowner(v=office.15)
ms:contentKeyID: 48600876
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.DistributionGroup.EndGetOwner
dev_langs:
- CSharp
- JScript
- VB
- other
---

# DistributionGroup.EndGetOwner method

Gets the owner of a group.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndGetOwner ( _
    asyncResult As IAsyncResult _
) As Contact
'Usage
Dim instance As DistributionGroup
Dim asyncResult As IAsyncResult
Dim returnValue As Contact

returnValue = instance.EndGetOwner(asyncResult)
```

``` csharp
public Contact EndGetOwner(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

## See also

#### Reference

[DistributionGroup class](distributiongroup-class-microsoft-lync-model-group_2.md)

[DistributionGroup members](distributiongroup-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

