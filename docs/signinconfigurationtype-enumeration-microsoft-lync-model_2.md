---
title: SignInConfigurationType enumeration (Microsoft.Lync.Model)
TOCTitle: SignInConfigurationType enumeration
ms:assetid: T:Microsoft.Lync.Model.SignInConfigurationType_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.signinconfigurationtype_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595426
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SignInConfigurationType
- Microsoft.Lync.Model.SignInConfigurationType.ExternalServer
- Microsoft.Lync.Model.SignInConfigurationType.InternalServer
- Microsoft.Lync.Model.SignInConfigurationType.Invalid
- Microsoft.Lync.Model.SignInConfigurationType.Mode
- Microsoft.Lync.Model.SignInConfigurationType.SavePassword
- Microsoft.Lync.Model.SignInConfigurationType.Transport
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SignInConfigurationType enumeration

Enumerates sign in configuration setting types.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration SignInConfigurationType
'Usage
Dim instance As SignInConfigurationType
```

``` csharp
public enum SignInConfigurationType
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
<td>Mode</td>
<td>A flag indicating whether the configuration mode is settable.</td>
</tr>
<tr class="even">
<td></td>
<td>Transport</td>
<td>A flag indicating whether the transport mode is settable.</td>
</tr>
<tr class="odd">
<td></td>
<td>InternalServer</td>
<td>A flag indicating whether the server internal address is settable.</td>
</tr>
<tr class="even">
<td></td>
<td>ExternalServer</td>
<td>A flag indicating whether the server external address is settable.</td>
</tr>
<tr class="odd">
<td></td>
<td>SavePassword</td>
<td>A flag indicating whether the password can be saved.</td>
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

