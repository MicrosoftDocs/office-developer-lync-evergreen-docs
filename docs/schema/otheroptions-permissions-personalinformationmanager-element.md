﻿---
title: otherOptions/Permissions/personalInformationManager element
TOCTitle: otherOptions/Permissions/personalInformationManager element
ms:assetid: 335fa09e-85fc-405e-aeaf-9d5bb3c3bd6a
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454757(v=office.15)
ms:contentKeyID: 57093808
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# otherOptions/Permissions/personalInformationManager element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the personal information manager.

```xml
<oo:personalInformationManager 
     xmlns:oo="http://schemas.microsoft.com/2006/09/sip/options/otherOptions">PIM token</oo:personalInformationManager>
```

oo:personalInformationManagerEnumEx

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
<td><p><a href="otheroptions-permissions-element.md">otherOptions/permissions element</a></p></td>
<td><p>The permissions property of an otherOptions category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

A oo:personalInformationManagerEnumEx token.

## Remarks

Microsoft Lync 2013 recognizes the following tokens:

  - none  
    Personal information manager is not specified.

  - outlook  
    Personal information manager is Microsoft Outlook.

  - wab  
    Personal information manager is WAB.

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

