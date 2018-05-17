---
title: ContactManager.BeginAddGroup method (DistributionGroup, AsyncCallback, Object) (Microsoft.Lync.Model)
TOCTitle: BeginAddGroup method (DistributionGroup, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.ContactManager.BeginAddGroup(Microsoft.Lync.Model.Group.DistributionGroup,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.beginaddgroup(v=office.15)
ms:contentKeyID: 48592901
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# ContactManager.BeginAddGroup method (DistributionGroup, AsyncCallback, Object)

Adds a distribution group to the group list.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginAddGroup ( _
    distributionGroup As DistributionGroup, _
    contactsAndGroupsCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ContactManager
Dim distributionGroup As DistributionGroup
Dim contactsAndGroupsCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginAddGroup(distributionGroup, _
    contactsAndGroupsCallback, state)
```

``` csharp
public IAsyncResult BeginAddGroup(
    DistributionGroup distributionGroup,
    AsyncCallback contactsAndGroupsCallback,
    Object state
)
```

#### Parameters

  - distributionGroup  
    Type: [Microsoft.Lync.Model.Group.DistributionGroup](distributiongroup-class-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - contactsAndGroupsCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[BeginAddGroup overload](contactmanager-beginaddgroup-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

