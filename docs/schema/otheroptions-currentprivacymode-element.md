---
title: otherOptions/currentPrivacyMode element
TOCTitle: otherOptions/currentPrivacyMode element
ms:assetid: e5834cdb-dd95-40dd-81fc-5ba57266fcc5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454771(v=office.15)
ms:contentKeyID: 57093658
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# otherOptions/currentPrivacyMode element


**Applies to:** Lync 2013 | Lync Server 2013

Contains the currently selected privacy mode.

``` xml
<privacyModeUserSelection>privacyModeUserSelectionEnumEx</privacyModeUserSelection>
```

privacyModeEnumEx

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

A privacyModeEnumEx value.

## Remarks

This is introduced in the Microsoft Lync Server 2010 release.

Microsoft Lync 2013 recognizes the following privacy mode tokens:

  - migratingToPrivacy  

  - migratingToStandard  

  - private  

  - standard  

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

