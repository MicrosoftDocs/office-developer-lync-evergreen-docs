---
title: LyncClient.BeginInitialize method  (Microsoft.Lync.Model)
TOCTitle: 'BeginInitialize method '
ms:assetid: M:Microsoft.Lync.Model.LyncClient.BeginInitialize(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclient.begininitialize(v=office.15)
ms:contentKeyID: 48590628
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.LyncClient.BeginInitialize
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncClient.BeginInitialize method

Initializes LyncClient when the Lync is in Suppressed Mode. You do not call this method when Lync is not suppressed.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginInitialize ( _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As LyncClient
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginInitialize(callback, _
    state)
```

``` csharp
public IAsyncResult BeginInitialize(
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - callback  
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

