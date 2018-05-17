---
title: SignInConfiguration.TransportMode property  (Microsoft.Lync.Model)
TOCTitle: 'TransportMode property '
ms:assetid: P:Microsoft.Lync.Model.SignInConfiguration.TransportMode_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.signinconfiguration.transportmode_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592920
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SignInConfiguration.TransportMode
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SignInConfiguration.TransportMode property

Sets the current server transport.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Property TransportMode As TransportMode
    Get
    Set
'Usage
Dim instance As SignInConfiguration
Dim value As TransportMode

value = instance.TransportMode

instance.TransportMode = value
```

``` csharp
public TransportMode TransportMode { get; set; }
```

#### Property value

Type: [Microsoft.Lync.Model.TransportMode](transportmode-enumeration-microsoft-lync-model_2.md)  

## Remarks

This property cannot be set. Attempting to do so raises the NotSupportedException.

## See also

#### Reference

[SignInConfiguration class](signinconfiguration-class-microsoft-lync-model_2.md)

[SignInConfiguration members](signinconfiguration-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

