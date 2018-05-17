---
title: AccessPermission.AccessEntries property  (Microsoft.Lync.Model)
TOCTitle: 'AccessEntries property '
ms:assetid: P:Microsoft.Lync.Model.AccessPermission.AccessEntries_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.accesspermission.accessentries_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600331
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AccessPermission.AccessEntries
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AccessPermission.AccessEntries property

Returns all access entries.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property AccessEntries As IList(Of AccessEntry)
    Get
'Usage
Dim instance As AccessPermission
Dim value As IList(Of AccessEntry)

value = instance.AccessEntries
```

``` csharp
public IList<AccessEntry> AccessEntries { get; }
```

#### Property value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[AccessEntry](accessentry-class-microsoft-lync-model_2.md)\>  

## See also

#### Reference

[AccessPermission class](accesspermission-class-microsoft-lync-model_2.md)

[AccessPermission members](accesspermission-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

