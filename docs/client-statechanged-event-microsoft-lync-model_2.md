---
title: Client.StateChanged event (Microsoft.Lync.Model)
TOCTitle: StateChanged event
ms:assetid: E:Microsoft.Lync.Model.Client.StateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.client.statechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596788
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Client.StateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Client.StateChanged event

Occurs when the Client state changes.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event StateChanged As EventHandler(Of ClientStateChangedEventArgs)
'Usage
Dim instance As Client
Dim handler As EventHandler(Of ClientStateChangedEventArgs)

AddHandler instance.StateChanged, handler
```

``` csharp
public event EventHandler<ClientStateChangedEventArgs> StateChanged
```

## See also

#### Reference

[Client class](client-class-microsoft-lync-model_2.md)

[Client members](client-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

