---
title: SearchProviders enumeration (Microsoft.Lync.Model)
TOCTitle: SearchProviders enumeration
ms:assetid: T:Microsoft.Lync.Model.SearchProviders_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.searchproviders_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599813
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SearchProviders
- Microsoft.Lync.Model.SearchProviders.Default
- Microsoft.Lync.Model.SearchProviders.GlobalAddressList
- Microsoft.Lync.Model.SearchProviders.Expert
- Microsoft.Lync.Model.SearchProviders.ExchangeService
- Microsoft.Lync.Model.SearchProviders.Invalid
- Microsoft.Lync.Model.SearchProviders.OtherContacts
- Microsoft.Lync.Model.SearchProviders.PersonalContacts
- Microsoft.Lync.Model.SearchProviders.WindowsAddressBook
- Microsoft.Lync.Model.SearchProviders.Reserved1
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchProviders enumeration

Enumerates the search provider types.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration SearchProviders
'Usage
Dim instance As SearchProviders
```

``` csharp
[FlagsAttribute]
public enum SearchProviders
```

## Members

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
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
<td>Default</td>
<td>Searches in the default location Obsolete.
<p>This search provider is deprecated in all releases after Lync 2010.</p></td>
</tr>
<tr class="even">
<td></td>
<td>ExchangeService</td>
<td>Searches in the Exchange Service contacts. Obsolete.
<p>This search provider is deprecated in all releases after Lync 2010.</p></td>
</tr>
<tr class="odd">
<td></td>
<td>GlobalAddressList</td>
<td>Searches in the Global Address List. Obsolete.
<p>This search provider is deprecated in all releases after Lync 2010.</p></td>
</tr>
<tr class="even">
<td></td>
<td>WindowsAddressBook</td>
<td>Searches in the Windows Address Book. Obsolete.
<p>This search provider is deprecated in all releases after Lync 2010.</p></td>
</tr>
<tr class="odd">
<td></td>
<td>OtherContacts</td>
<td>Searches for Contacts that are neither in custom groups nor in other address lists. Obsolete.
<p>This search provider is deprecated in all releases after Lync 2010.</p></td>
</tr>
<tr class="even">
<td></td>
<td>PersonalContacts</td>
<td>Searches in the Windows Address Book and in the Exchange Service contacts. Obsolete
<p>This search provider is deprecated in all releases after Lync 2010.</p></td>
</tr>
<tr class="odd">
<td></td>
<td>Expert</td>
<td>Expert search by keywords.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved1</td>
<td></td>
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

