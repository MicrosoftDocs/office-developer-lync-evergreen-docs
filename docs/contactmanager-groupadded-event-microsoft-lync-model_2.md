---
title: ContactManager.GroupAdded event (Microsoft.Lync.Model)
TOCTitle: GroupAdded event
ms:assetid: E:Microsoft.Lync.Model.ContactManager.GroupAdded_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.groupadded_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600200
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactManager.GroupAdded
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactManager.GroupAdded event

Occurs when a group is added.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event GroupAdded As EventHandler(Of GroupCollectionChangedEventArgs)
'Usage
Dim instance As ContactManager
Dim handler As EventHandler(Of GroupCollectionChangedEventArgs)

AddHandler instance.GroupAdded, handler
```

``` csharp
public event EventHandler<GroupCollectionChangedEventArgs> GroupAdded
```

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

