---
title: Utilities.CanInvoke method  (Microsoft.Lync.Model)
TOCTitle: 'CanInvoke method '
ms:assetid: M:Microsoft.Lync.Model.Utilities.CanInvoke(Microsoft.Lync.Model.UtilitiesAction,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.utilities.caninvoke(v=office.15)
ms:contentKeyID: 48598123
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Utilities.CanInvoke
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Utilities.CanInvoke method

Returns true if the utility action can be invoked.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanInvoke ( _
    utilitiesAction As UtilitiesAction, _
    actionContext As Object _
) As Boolean
'Usage
Dim instance As Utilities
Dim utilitiesAction As UtilitiesAction
Dim actionContext As Object
Dim returnValue As Boolean

returnValue = instance.CanInvoke(utilitiesAction, _
    actionContext)
```

``` csharp
public bool CanInvoke(
    UtilitiesAction utilitiesAction,
    Object actionContext
)
```

#### Parameters

  - utilitiesAction  
    Type: [Microsoft.Lync.Model.UtilitiesAction](utilitiesaction-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - actionContext  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[Utilities class](utilities-class-microsoft-lync-model_2.md)

[Utilities members](utilities-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

