---
title: CustomGroup.BeginRename method  (Microsoft.Lync.Model.Group)
TOCTitle: 'BeginRename method '
ms:assetid: M:Microsoft.Lync.Model.Group.CustomGroup.BeginRename(System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.customgroup.beginrename(v=office.15)
ms:contentKeyID: 48602033
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.CustomGroup.BeginRename
dev_langs:
- CSharp
- JScript
- VB
- other
---

# CustomGroup.BeginRename method

Renames the custom group.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginRename ( _
    newName As String, _
    groupCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As CustomGroup
Dim newName As String
Dim groupCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginRename(newName, _
    groupCallback, state)
```

``` csharp
public IAsyncResult BeginRename(
    string newName,
    AsyncCallback groupCallback,
    Object state
)
```

#### Parameters

  - newName  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - groupCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[CustomGroup class](customgroup-class-microsoft-lync-model-group_2.md)

[CustomGroup members](customgroup-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

