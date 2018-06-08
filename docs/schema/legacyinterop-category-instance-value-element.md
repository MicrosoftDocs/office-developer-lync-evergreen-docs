---
title: legacyInterop category instance value element
TOCTitle: legacyInterop category instance value element
ms:assetid: 1d9ac6c5-a5bd-43d4-ac1b-e3335a1723c9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454762(v=office.15)
ms:contentKeyID: 57093649
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# legacyInterop category instance value element


**Applies to:** Lync 2013 | Lync Server 2013

Represents the aggregated presence state for interoperating with legacy clients.

```xml
<legacyInterop xmlns:xs=”http://www.w3.org/2001/XMLSchema”
 xmlns="http://schemas.microsoft.com/2006/09/sip/categories" 
   availability=”xs:unsignedInt” 
   token=”xs:token”/>
```

legacyInteropType

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Attribute</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>availability</p></td>
<td><p>Required attribute to specify the availability number corresponding to that of the <a href="state-element_4.md">state[@type='aggregateState'] element</a> category instance.</p></td>
</tr>
<tr class="even">
<td><p>token</p></td>
<td><p>Optional attribute to specify the activity token corresponding to that of the <a href="state-element_4.md">state[@type='aggregateState'] element</a> category instance.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


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
<td><p>None</p></td>
<td><p>This is a top-level element as an enhanced presence category instance</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

This is a private category instance published by the server to support interoperation with legacy clients.

## Example

The following XML code snippet shows an Offline (availability=18500) presence state.

    <legacyInterop availability="18500" xmlns="http://schemas.microsoft.com/2006/09/sip/categories" />

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/categories</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>legacyInterop</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p></p></td>
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

