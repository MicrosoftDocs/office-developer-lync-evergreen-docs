---
title: AccessPermission.AccessEntryRemoved event (Microsoft.Lync.Model)
TOCTitle: AccessEntryRemoved event
ms:assetid: E:Microsoft.Lync.Model.AccessPermission.AccessEntryRemoved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.accesspermission.accessentryremoved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594925
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AccessPermission.AccessEntryRemoved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AccessPermission.AccessEntryRemoved event

Raised when an access entry is removed.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event AccessEntryRemoved As EventHandler(Of AccessEntryCollectionChangedEventArgs)
'Usage
Dim instance As AccessPermission
Dim handler As EventHandler(Of AccessEntryCollectionChangedEventArgs)

AddHandler instance.AccessEntryRemoved, handler
```

``` csharp
public event EventHandler<AccessEntryCollectionChangedEventArgs> AccessEntryRemoved
```

## See also

#### Reference

[AccessPermission class](accesspermission-class-microsoft-lync-model_2.md)

[AccessPermission members](accesspermission-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

