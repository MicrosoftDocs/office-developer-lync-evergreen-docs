---
title: SignInConfiguration.IsPasswordSaved property  (Microsoft.Lync.Model)
TOCTitle: 'IsPasswordSaved property '
ms:assetid: P:Microsoft.Lync.Model.SignInConfiguration.IsPasswordSaved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.signinconfiguration.ispasswordsaved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590570
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SignInConfiguration.IsPasswordSaved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SignInConfiguration.IsPasswordSaved property

Returns true if Lync client saves a user sign in password

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Property IsPasswordSaved As Boolean
    Get
    Set
'Usage
Dim instance As SignInConfiguration
Dim value As Boolean

value = instance.IsPasswordSaved

instance.IsPasswordSaved = value
```

``` csharp
public bool IsPasswordSaved { get; set; }
```

#### Property value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## Remarks

Although this is a read/write property, writing a value to this property has no effect on the client.

## See also

#### Reference

[SignInConfiguration class](signinconfiguration-class-microsoft-lync-model_2.md)

[SignInConfiguration members](signinconfiguration-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

