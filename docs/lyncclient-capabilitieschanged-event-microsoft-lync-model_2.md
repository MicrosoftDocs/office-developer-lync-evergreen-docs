---
title: LyncClient.CapabilitiesChanged event (Microsoft.Lync.Model)
TOCTitle: CapabilitiesChanged event
ms:assetid: E:Microsoft.Lync.Model.LyncClient.CapabilitiesChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclient.capabilitieschanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591749
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.LyncClient.CapabilitiesChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncClient.CapabilitiesChanged event

Raised when the preferred capabilities changed

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event CapabilitiesChanged As EventHandler(Of PreferredCapabilitiesChangedEventArgs)
'Usage
Dim instance As LyncClient
Dim handler As EventHandler(Of PreferredCapabilitiesChangedEventArgs)

AddHandler instance.CapabilitiesChanged, handler
```

``` csharp
public event EventHandler<PreferredCapabilitiesChangedEventArgs> CapabilitiesChanged
```

## See also

#### Reference

[LyncClient class](lyncclient-class-microsoft-lync-model_2.md)

[LyncClient members](lyncclient-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

