---
title: AccessPermission.AccessEntryAdded event (Microsoft.Lync.Model)
TOCTitle: AccessEntryAdded event
ms:assetid: E:Microsoft.Lync.Model.AccessPermission.AccessEntryAdded_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.accesspermission.accessentryadded_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596802
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AccessPermission.AccessEntryAdded
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AccessPermission.AccessEntryAdded event

Raised when an access entry is added.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event AccessEntryAdded As EventHandler(Of AccessEntryCollectionChangedEventArgs)
'Usage
Dim instance As AccessPermission
Dim handler As EventHandler(Of AccessEntryCollectionChangedEventArgs)

AddHandler instance.AccessEntryAdded, handler
```

``` csharp
public event EventHandler<AccessEntryCollectionChangedEventArgs> AccessEntryAdded
```

## See also

#### Reference

[AccessPermission class](accesspermission-class-microsoft-lync-model_2.md)

[AccessPermission members](accesspermission-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

