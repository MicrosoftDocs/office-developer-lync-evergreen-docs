---
title: AccessEntry.CanSetPermission method  (Microsoft.Lync.Model)
TOCTitle: 'CanSetPermission method '
ms:assetid: M:Microsoft.Lync.Model.AccessEntry.CanSetPermission(Microsoft.Lync.Model.AccessPermission)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.accessentry.cansetpermission(v=office.15)
ms:contentKeyID: 48602065
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AccessEntry.CanSetPermission
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AccessEntry.CanSetPermission method

Returns true when allowed to set to a specific permission.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanSetPermission ( _
    permission As AccessPermission _
) As Boolean
'Usage
Dim instance As AccessEntry
Dim permission As AccessPermission
Dim returnValue As Boolean

returnValue = instance.CanSetPermission(permission)
```

``` csharp
public bool CanSetPermission(
    AccessPermission permission
)
```

#### Parameters

  - permission  
    Type: [Microsoft.Lync.Model.AccessPermission](accesspermission-class-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[AccessEntry class](accessentry-class-microsoft-lync-model_2.md)

[AccessEntry members](accessentry-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

