---
title: ContactSourceTypes enumeration (Microsoft.Lync.Model)
TOCTitle: ContactSourceTypes enumeration
ms:assetid: T:Microsoft.Lync.Model.ContactSourceTypes_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactsourcetypes_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597143
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactSourceTypes
- Microsoft.Lync.Model.ContactSourceTypes.ExchangeService
- Microsoft.Lync.Model.ContactSourceTypes.GlobalAddressList
- Microsoft.Lync.Model.ContactSourceTypes.Invalid
- Microsoft.Lync.Model.ContactSourceTypes.Unknown
- Microsoft.Lync.Model.ContactSourceTypes.WindowsAddressBook
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSourceTypes enumeration

Enumerates the contact provider type.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration ContactSourceTypes
'Usage
Dim instance As ContactSourceTypes
```

``` csharp
[FlagsAttribute]
public enum ContactSourceTypes
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
<td>Unknown</td>
<td>The contact source is unknown.</td>
</tr>
<tr class="even">
<td></td>
<td>GlobalAddressList</td>
<td>The contact source is the Global Address List.</td>
</tr>
<tr class="odd">
<td></td>
<td>WindowsAddressBook</td>
<td>The contact source is the Windows Address Book.</td>
</tr>
<tr class="even">
<td></td>
<td>ExchangeService</td>
<td>The contact source is the Exchange Service.</td>
</tr>
<tr class="odd">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

