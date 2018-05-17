---
title: DistributionGroup.BeginGetAllMembers method  (Microsoft.Lync.Model.Group)
TOCTitle: 'BeginGetAllMembers method '
ms:assetid: M:Microsoft.Lync.Model.Group.DistributionGroup.BeginGetAllMembers(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.distributiongroup.begingetallmembers(v=office.15)
ms:contentKeyID: 48592300
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.DistributionGroup.BeginGetAllMembers
dev_langs:
- CSharp
- JScript
- VB
- other
---

# DistributionGroup.BeginGetAllMembers method

Gets all group members.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginGetAllMembers ( _
    groupCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As DistributionGroup
Dim groupCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginGetAllMembers(groupCallback, _
    state)
```

``` csharp
public IAsyncResult BeginGetAllMembers(
    AsyncCallback groupCallback,
    Object state
)
```

#### Parameters

  - groupCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[DistributionGroup class](distributiongroup-class-microsoft-lync-model-group_2.md)

[DistributionGroup members](distributiongroup-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

