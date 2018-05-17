---
title: LyncClient.BeginSignIn method  (Microsoft.Lync.Model)
TOCTitle: 'BeginSignIn method '
ms:assetid: M:Microsoft.Lync.Model.LyncClient.BeginSignIn(System.String,System.String,System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclient.beginsignin(v=office.15)
ms:contentKeyID: 48592792
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.LyncClient.BeginSignIn
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncClient.BeginSignIn method

Starts the uc Client sign in process with a specific availability.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSignIn ( _
    userUri As String, _
    domainAndUsername As String, _
    password As String, _
    communicatorClientCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As LyncClient
Dim userUri As String
Dim domainAndUsername As String
Dim password As String
Dim communicatorClientCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSignIn(userUri, _
    domainAndUsername, password, communicatorClientCallback, _
    state)
```

``` csharp
public IAsyncResult BeginSignIn(
    string userUri,
    string domainAndUsername,
    string password,
    AsyncCallback communicatorClientCallback,
    Object state
)
```

#### Parameters

  - userUri  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - domainAndUsername  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - password  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - communicatorClientCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[LyncClient class](lyncclient-class-microsoft-lync-model_2.md)

[LyncClient members](lyncclient-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

