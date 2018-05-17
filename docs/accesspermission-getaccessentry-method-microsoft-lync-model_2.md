---
title: AccessPermission.GetAccessEntry method  (Microsoft.Lync.Model)
TOCTitle: 'GetAccessEntry method '
ms:assetid: M:Microsoft.Lync.Model.AccessPermission.GetAccessEntry(Microsoft.Lync.Model.AccessEntryScope,System.String,Microsoft.Lync.Model.AccessEntry@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.accesspermission.getaccessentry(v=office.15)
ms:contentKeyID: 48593822
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AccessPermission.GetAccessEntry
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AccessPermission.GetAccessEntry method

Gets the access entry instance, or creates a new one if not found.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub GetAccessEntry ( _
    scope As AccessEntryScope, _
    entryId As String, _
    <OutAttribute> ByRef accessEntry As AccessEntry _
)
'Usage
Dim instance As AccessPermission
Dim scope As AccessEntryScope
Dim entryId As String
Dim accessEntry As AccessEntry

instance.GetAccessEntry(scope, entryId, _
    accessEntry)
```

``` csharp
public void GetAccessEntry(
    AccessEntryScope scope,
    string entryId,
    out AccessEntry accessEntry
)
```

#### Parameters

  - scope  
    Type: [Microsoft.Lync.Model.AccessEntryScope](accessentryscope-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - entryId  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - accessEntry  
    Type: [Microsoft.Lync.Model.AccessEntry](accessentry-class-microsoft-lync-model_2.md)  

## See also

#### Reference

[AccessPermission class](accesspermission-class-microsoft-lync-model_2.md)

[AccessPermission members](accesspermission-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

