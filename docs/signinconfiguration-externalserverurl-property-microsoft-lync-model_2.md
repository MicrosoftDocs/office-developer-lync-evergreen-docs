---
title: SignInConfiguration.ExternalServerUrl property  (Microsoft.Lync.Model)
TOCTitle: 'ExternalServerUrl property '
ms:assetid: P:Microsoft.Lync.Model.SignInConfiguration.ExternalServerUrl_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.signinconfiguration.externalserverurl_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601758
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SignInConfiguration.ExternalServerUrl
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SignInConfiguration.ExternalServerUrl property

Sets the Lync server that a user signs in to when outside of an organization intranet.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Property ExternalServerUrl As String
    Get
    Set
'Usage
Dim instance As SignInConfiguration
Dim value As String

value = instance.ExternalServerUrl

instance.ExternalServerUrl = value
```

``` csharp
public string ExternalServerUrl { get; set; }
```

#### Property value

Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

## Remarks

This value is ignored when Mode is set to LyncClientConfigurationMode.Auto

## See also

#### Reference

[SignInConfiguration class](signinconfiguration-class-microsoft-lync-model_2.md)

[SignInConfiguration members](signinconfiguration-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

