---
title: SignInConfiguration.Mode property  (Microsoft.Lync.Model)
TOCTitle: 'Mode property '
ms:assetid: P:Microsoft.Lync.Model.SignInConfiguration.Mode_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.signinconfiguration.mode_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601201
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SignInConfiguration.Mode
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SignInConfiguration.Mode property

Sets or clears server auto-discovery mode.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Property Mode As LyncClientConfigurationMode
    Get
    Set
'Usage
Dim instance As SignInConfiguration
Dim value As LyncClientConfigurationMode

value = instance.Mode

instance.Mode = value
```

``` csharp
public LyncClientConfigurationMode Mode { get; set; }
```

#### Property value

Type: [Microsoft.Lync.Model.LyncClientConfigurationMode](lyncclientconfigurationmode-enumeration-microsoft-lync-model_2.md)  

## Remarks

When Mode is set to LyncClientConfigurationMode.Auto, Lync attempts to discover the Lync front end server to register on based on the supplied username SIP address.

## See also

#### Reference

[SignInConfiguration class](signinconfiguration-class-microsoft-lync-model_2.md)

[SignInConfiguration members](signinconfiguration-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

