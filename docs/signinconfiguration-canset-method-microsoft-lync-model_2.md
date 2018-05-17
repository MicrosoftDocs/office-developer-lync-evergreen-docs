---
title: SignInConfiguration.CanSet method  (Microsoft.Lync.Model)
TOCTitle: 'CanSet method '
ms:assetid: M:Microsoft.Lync.Model.SignInConfiguration.CanSet(Microsoft.Lync.Model.SignInConfigurationType)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.signinconfiguration.canset(v=office.15)
ms:contentKeyID: 48591760
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SignInConfiguration.CanSet
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SignInConfiguration.CanSet method

returns true if the configuration type is settable.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanSet ( _
    configurationType As SignInConfigurationType _
) As Boolean
'Usage
Dim instance As SignInConfiguration
Dim configurationType As SignInConfigurationType
Dim returnValue As Boolean

returnValue = instance.CanSet(configurationType)
```

``` csharp
public bool CanSet(
    SignInConfigurationType configurationType
)
```

#### Parameters

  - configurationType  
    Type: [Microsoft.Lync.Model.SignInConfigurationType](signinconfigurationtype-enumeration-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[SignInConfiguration class](signinconfiguration-class-microsoft-lync-model_2.md)

[SignInConfiguration members](signinconfiguration-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

