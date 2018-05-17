---
title: AccessPermission.TryGetValue method  (Microsoft.Lync.Model)
TOCTitle: 'TryGetValue method '
ms:assetid: M:Microsoft.Lync.Model.AccessPermission.TryGetValue(Microsoft.Lync.Model.AccessEntryScope,System.String,Microsoft.Lync.Model.AccessEntry@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.accesspermission.trygetvalue(v=office.15)
ms:contentKeyID: 48599839
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AccessPermission.TryGetValue
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AccessPermission.TryGetValue method

Try to get an access entry object given its scope and id.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function TryGetValue ( _
    scope As AccessEntryScope, _
    entryId As String, _
    <OutAttribute> ByRef accessEntry As AccessEntry _
) As Boolean
'Usage
Dim instance As AccessPermission
Dim scope As AccessEntryScope
Dim entryId As String
Dim accessEntry As AccessEntry
Dim returnValue As Boolean

returnValue = instance.TryGetValue(scope, _
    entryId, accessEntry)
```

``` csharp
public bool TryGetValue(
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

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[AccessPermission class](accesspermission-class-microsoft-lync-model_2.md)

[AccessPermission members](accesspermission-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

