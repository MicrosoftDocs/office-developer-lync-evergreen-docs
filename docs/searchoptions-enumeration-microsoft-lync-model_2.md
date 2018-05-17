---
title: SearchOptions enumeration (Microsoft.Lync.Model)
TOCTitle: SearchOptions enumeration
ms:assetid: T:Microsoft.Lync.Model.SearchOptions_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.searchoptions_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48593439
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SearchOptions
- Microsoft.Lync.Model.SearchOptions.ContactsOnly
- Microsoft.Lync.Model.SearchOptions.Default
- Microsoft.Lync.Model.SearchOptions.IncludeContactsWithoutSipOrTelUri
- Microsoft.Lync.Model.SearchOptions.Invalid
- Microsoft.Lync.Model.SearchOptions.MatchWholeWord
- Microsoft.Lync.Model.SearchOptions.Reserved1
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchOptions enumeration

Enumerates search options.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration SearchOptions
'Usage
Dim instance As SearchOptions
```

``` csharp
[FlagsAttribute]
public enum SearchOptions
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
<td>Default</td>
<td>The default option used for search.</td>
</tr>
<tr class="even">
<td></td>
<td>MatchWholeWord</td>
<td>Match the whole word instead of the prefix match.</td>
</tr>
<tr class="odd">
<td></td>
<td>ContactsOnly</td>
<td>Searching contacts only, ignore group matches.</td>
</tr>
<tr class="even">
<td></td>
<td>IncludeContactsWithoutSipOrTelUri</td>
<td>Allow contacts without SIP, email, or TEL addresses in the search results.</td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved1</td>
<td></td>
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

