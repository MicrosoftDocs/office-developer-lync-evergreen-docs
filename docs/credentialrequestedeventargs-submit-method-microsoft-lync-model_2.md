---
title: CredentialRequestedEventArgs.Submit method  (Microsoft.Lync.Model)
TOCTitle: 'Submit method '
ms:assetid: M:Microsoft.Lync.Model.CredentialRequestedEventArgs.Submit(System.String,System.String,System.Boolean)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.credentialrequestedeventargs.submit(v=office.15)
ms:contentKeyID: 48597141
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.CredentialRequestedEventArgs.Submit
dev_langs:
- CSharp
- JScript
- VB
- other
---

# CredentialRequestedEventArgs.Submit method

Apply the updated credential.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub Submit ( _
    domainAndUsername As String, _
    password As String, _
    savePassword As Boolean _
)
'Usage
Dim instance As CredentialRequestedEventArgs
Dim domainAndUsername As String
Dim password As String
Dim savePassword As Boolean

instance.Submit(domainAndUsername, password, _
    savePassword)
```

``` csharp
public void Submit(
    string domainAndUsername,
    string password,
    bool savePassword
)
```

#### Parameters

  - domainAndUsername  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - password  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - savePassword  
    Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## See also

#### Reference

[CredentialRequestedEventArgs class](credentialrequestedeventargs-class-microsoft-lync-model_2.md)

[CredentialRequestedEventArgs members](credentialrequestedeventargs-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

