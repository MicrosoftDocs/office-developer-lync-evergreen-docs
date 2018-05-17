---
title: CredentialRequestedEventArgs class (Microsoft.Lync.Model)
TOCTitle: CredentialRequestedEventArgs class
ms:assetid: T:Microsoft.Lync.Model.CredentialRequestedEventArgs_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.credentialrequestedeventargs_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598255
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.CredentialRequestedEventArgs
dev_langs:
- CSharp
- JScript
- VB
- other
---

# CredentialRequestedEventArgs class

CredentialRequestedEventData Class which is used to get the credential request type, domain and user names. The password, domain and user names can be changed from the event data object obtained from the event OnCredentialRequested.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.EventArgs](http://msdn2.microsoft.com/en-us/library/118wxtk3)  
    Microsoft.Lync.Model.CredentialRequestedEventArgs  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class CredentialRequestedEventArgs _
    Inherits EventArgs
'Usage
Dim instance As CredentialRequestedEventArgs
```

``` csharp
public class CredentialRequestedEventArgs : EventArgs
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[CredentialRequestedEventArgs members](credentialrequestedeventargs-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

