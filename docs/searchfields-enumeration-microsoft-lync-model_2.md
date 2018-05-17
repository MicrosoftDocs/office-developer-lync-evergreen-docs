---
title: SearchFields enumeration (Microsoft.Lync.Model)
TOCTitle: SearchFields enumeration
ms:assetid: T:Microsoft.Lync.Model.SearchFields_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.searchfields_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596362
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SearchFields.Alias
- Microsoft.Lync.Model.SearchFields.Invalid
- Microsoft.Lync.Model.SearchFields.FirstName
- Microsoft.Lync.Model.SearchFields.PhoneNumbers
- Microsoft.Lync.Model.SearchFields
- Microsoft.Lync.Model.SearchFields.PhoneExtention
- Microsoft.Lync.Model.SearchFields.AllFields
- Microsoft.Lync.Model.SearchFields.LastName
- Microsoft.Lync.Model.SearchFields.EmailAddresses
- Microsoft.Lync.Model.SearchFields.Company
- Microsoft.Lync.Model.SearchFields.PrimaryEmailAddress
- Microsoft.Lync.Model.SearchFields.DisplayName
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchFields enumeration

Enumerates search filter properties.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration SearchFields
'Usage
Dim instance As SearchFields
```

``` csharp
[FlagsAttribute]
public enum SearchFields
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
<td>FirstName</td>
<td>Search against first name if indexed.</td>
</tr>
<tr class="even">
<td></td>
<td>LastName</td>
<td>Search against last name if indexed.</td>
</tr>
<tr class="odd">
<td></td>
<td>DisplayName</td>
<td>Search against display name if indexed, several forms of display name may or may not supported by search provider</td>
</tr>
<tr class="even">
<td></td>
<td>Company</td>
<td>Search against company name if indexed.</td>
</tr>
<tr class="odd">
<td></td>
<td>PrimaryEmailAddress</td>
<td>Search against primary email address if indexed.</td>
</tr>
<tr class="even">
<td></td>
<td>EmailAddresses</td>
<td>Search against all email addresses if indexed.</td>
</tr>
<tr class="odd">
<td></td>
<td>Alias</td>
<td>Search against alias if indexed.</td>
</tr>
<tr class="even">
<td></td>
<td>PhoneNumbers</td>
<td>Search against phone numbers if indexed.</td>
</tr>
<tr class="odd">
<td></td>
<td>PhoneExtention</td>
<td>Search against phone numbers if indexed.</td>
</tr>
<tr class="even">
<td></td>
<td>AllFields</td>
<td>Search against any indexed field.</td>
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

