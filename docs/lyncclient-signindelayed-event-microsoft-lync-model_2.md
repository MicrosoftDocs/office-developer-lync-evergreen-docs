---
title: LyncClient.SignInDelayed event (Microsoft.Lync.Model)
TOCTitle: SignInDelayed event
ms:assetid: E:Microsoft.Lync.Model.LyncClient.SignInDelayed_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclient.signindelayed_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600956
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.LyncClient.SignInDelayed
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncClient.SignInDelayed event

Raised when there is a delay in the SignIn/auto-recover process

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event SignInDelayed As EventHandler(Of SignInDelayedEventArgs)
'Usage
Dim instance As LyncClient
Dim handler As EventHandler(Of SignInDelayedEventArgs)

AddHandler instance.SignInDelayed, handler
```

``` csharp
public event EventHandler<SignInDelayedEventArgs> SignInDelayed
```

## See also

#### Reference

[LyncClient class](lyncclient-class-microsoft-lync-model_2.md)

[LyncClient members](lyncclient-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

