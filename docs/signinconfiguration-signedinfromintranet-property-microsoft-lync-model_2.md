---
title: SignInConfiguration.SignedInFromIntranet property  (Microsoft.Lync.Model)
TOCTitle: 'SignedInFromIntranet property '
ms:assetid: P:Microsoft.Lync.Model.SignInConfiguration.SignedInFromIntranet_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.signinconfiguration.signedinfromintranet_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591742
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SignInConfiguration.SignedInFromIntranet
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SignInConfiguration.SignedInFromIntranet property

Determines whether user signed in from intranet or not.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property SignedInFromIntranet As Boolean
    Get
'Usage
Dim instance As SignInConfiguration
Dim value As Boolean

value = instance.SignedInFromIntranet
```

``` csharp
public bool SignedInFromIntranet { get; }
```

#### Property value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## Remarks

If a user is not signed in to Lync, the property returns false.

## See also

#### Reference

[SignInConfiguration class](signinconfiguration-class-microsoft-lync-model_2.md)

[SignInConfiguration members](signinconfiguration-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

