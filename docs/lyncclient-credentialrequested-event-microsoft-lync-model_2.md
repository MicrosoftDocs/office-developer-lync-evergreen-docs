---
title: LyncClient.CredentialRequested event (Microsoft.Lync.Model)
TOCTitle: CredentialRequested event
ms:assetid: E:Microsoft.Lync.Model.LyncClient.CredentialRequested_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclient.credentialrequested_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591173
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.LyncClient.CredentialRequested
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncClient.CredentialRequested event

Raised when a user credential is requested by a server such as the Lync server.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event CredentialRequested As EventHandler(Of CredentialRequestedEventArgs)
'Usage
Dim instance As LyncClient
Dim handler As EventHandler(Of CredentialRequestedEventArgs)

AddHandler instance.CredentialRequested, handler
```

``` csharp
public event EventHandler<CredentialRequestedEventArgs> CredentialRequested
```

## Remarks

This event is only raised when Lync client is in Full UI supression mode and a user has not provided acceptable sign-in credentials or other credential types requested by othe r servers. When not in UI suppression mode, this even is not raised when credentials are requested. In this case, the Lync client presents a credential request dialog.

## See also

#### Reference

[LyncClient class](lyncclient-class-microsoft-lync-model_2.md)

[LyncClient members](lyncclient-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

