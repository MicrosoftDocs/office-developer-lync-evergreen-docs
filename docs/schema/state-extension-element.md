---
title: state/extension element
TOCTitle: state/extension element
ms:assetid: 2460757d-6335-4e10-9783-e514ef919c2e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454812(v=office.15)
ms:contentKeyID: 57093962
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state/extension element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies an application-specific extension to a presence state element.

``` xml
<st:extension xmlns:st="http://schemas.microsoft.com/2006/09/sip/state" >
   <[any]>any element</[any]>
</st:extension>
```

st:extensionType

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

#### Child elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Occurrence</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[any]</p></td>
<td><p>1 or more</p></td>
<td><p>Availability number indicating the presence status.</p></td>
</tr>
</tbody>
</table>


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
<td><p><a href="state-category-instance-value-elements.md">state category instance value elements</a></p></td>
<td><p>An enhanced presence state category instance value with a custom extension.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/state</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>state</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>state.xsd, statetypes.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Category instance elements for presence](category-instance-elements-for-presence.md)

[state category instance value elements](state-category-instance-value-elements.md)

#### Other resources

Presence State and state Category Instances

