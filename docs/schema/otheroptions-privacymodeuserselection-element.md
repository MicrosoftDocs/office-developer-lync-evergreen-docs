---
title: otherOptions/privacyModeUserSelection element
TOCTitle: otherOptions/privacyModeUserSelection element
ms:assetid: f84dbfdb-ea55-46c7-b939-f3a1b01f793a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454770(v=office.15)
ms:contentKeyID: 57093657
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# otherOptions/privacyModeUserSelection element


_**Applies to:** Lync 2013 | Lync Server 2013_

Contains a token showing the user selection of a privacy mode.

``` xml
    <privacyModeUserSelection>privacyModeUserSelectionEnumEx</privacyModeUserSelection>
```

privacyModeUserSelectionEnumEx

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

#### Child elements

None

#### Parent elements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a></p></td>
<td><p>otherOptions category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

A privacyModeUserSelectionEnumEx value.

## Remarks

This is introduced in the Microsoft Lync Server 2010 release.

Microsoft Lync 2013 recognizes the following pivacyModeUserSelection tokens:

  - noSelection  
    User has not selected any privacy mode.

  - private  
    User selection of the privacy mode is private.

  - standard  
    User selection of the privacy mode is standard.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/options/otherOptions</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>options-otherOptions</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>options-otherOptions.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[otherOptions category instance value element](otheroptions-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

