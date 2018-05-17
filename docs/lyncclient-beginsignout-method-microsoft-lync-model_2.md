---
title: LyncClient.BeginSignOut method  (Microsoft.Lync.Model)
TOCTitle: 'BeginSignOut method '
ms:assetid: M:Microsoft.Lync.Model.LyncClient.BeginSignOut(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclient.beginsignout(v=office.15)
ms:contentKeyID: 48599152
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.LyncClient.BeginSignOut
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncClient.BeginSignOut method

Starts the uc Client sign out process.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSignOut ( _
    communicatorClientCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As LyncClient
Dim communicatorClientCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSignOut(communicatorClientCallback, _
    state)
```

``` csharp
public IAsyncResult BeginSignOut(
    AsyncCallback communicatorClientCallback,
    Object state
)
```

#### Parameters

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

