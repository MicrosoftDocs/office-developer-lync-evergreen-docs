---
title: ContactManager.GroupRemoved event (Microsoft.Lync.Model)
TOCTitle: GroupRemoved event
ms:assetid: E:Microsoft.Lync.Model.ContactManager.GroupRemoved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.groupremoved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597608
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactManager.GroupRemoved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactManager.GroupRemoved event

Occurs when a group is removed.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event GroupRemoved As EventHandler(Of GroupCollectionChangedEventArgs)
'Usage
Dim instance As ContactManager
Dim handler As EventHandler(Of GroupCollectionChangedEventArgs)

AddHandler instance.GroupRemoved, handler
```

``` csharp
public event EventHandler<GroupCollectionChangedEventArgs> GroupRemoved
```

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

