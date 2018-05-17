---
title: ClientState enumeration (Microsoft.Lync.Model)
TOCTitle: ClientState enumeration
ms:assetid: T:Microsoft.Lync.Model.ClientState_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.clientstate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594389
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ClientState
- Microsoft.Lync.Model.ClientState.Initializing
- Microsoft.Lync.Model.ClientState.SigningOut
- Microsoft.Lync.Model.ClientState.SignedIn
- Microsoft.Lync.Model.ClientState.Invalid
- Microsoft.Lync.Model.ClientState.Uninitialized
- Microsoft.Lync.Model.ClientState.SignedOut
- Microsoft.Lync.Model.ClientState.ShuttingDown
- Microsoft.Lync.Model.ClientState.SigningIn
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ClientState enumeration

Enumerates the SignIn states of the Lync client.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ClientState
'Usage
Dim instance As ClientState
```

``` csharp
public enum ClientState
```

## Members

<table>
<thead>
<tr class="header">
<th></th>
<th>Member name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td>Uninitialized</td>
<td>Client is in uninitialized state</td>
</tr>
<tr class="even">
<td></td>
<td>SignedOut</td>
<td>Client is in signed out state.</td>
</tr>
<tr class="odd">
<td></td>
<td>SigningIn</td>
<td>Client is in signing in state.</td>
</tr>
<tr class="even">
<td></td>
<td>SignedIn</td>
<td>Client is in signed in state.</td>
</tr>
<tr class="odd">
<td></td>
<td>SigningOut</td>
<td>Client is in signing out state.</td>
</tr>
<tr class="even">
<td></td>
<td>ShuttingDown</td>
<td>Client is in shutting down state.</td>
</tr>
<tr class="odd">
<td></td>
<td>Initializing</td>
<td>Client is initializing.</td>
</tr>
<tr class="even">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

