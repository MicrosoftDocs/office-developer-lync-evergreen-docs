---
title: Self.Permissions property  (Microsoft.Lync.Model)
TOCTitle: 'Permissions property '
ms:assetid: P:Microsoft.Lync.Model.Self.Permissions_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.self.permissions_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48593870
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Self.Permissions
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Self.Permissions property

Gets the permission collection.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Permissions As IList(Of AccessPermission)
    Get
'Usage
Dim instance As Self
Dim value As IList(Of AccessPermission)

value = instance.Permissions
```

``` csharp
public IList<AccessPermission> Permissions { get; }
```

#### Property value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[AccessPermission](accesspermission-class-microsoft-lync-model_2.md)\>  

## See also

#### Reference

[Self class](self-class-microsoft-lync-model_2.md)

[Self members](self-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

