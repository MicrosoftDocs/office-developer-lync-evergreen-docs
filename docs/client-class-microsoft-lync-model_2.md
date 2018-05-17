---
title: Client class (Microsoft.Lync.Model)
TOCTitle: Client class
ms:assetid: T:Microsoft.Lync.Model.Client_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.client_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48588595
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Client
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Client class

Abstract client class which represents the main entry point for the API. Represents the Lync client and provides access to conversations and contacts via their respective manager classes.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWFull**  
        Microsoft.Lync.Model.Client  
          [Microsoft.Lync.Model.DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md)  
          [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md)  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public MustInherit Class Client _
    Inherits UCWFull
'Usage
Dim instance As Client
```

``` csharp
public abstract class Client : UCWFull
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[Client members](client-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

