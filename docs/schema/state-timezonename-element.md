---
title: state/timeZoneName element
TOCTitle: state/timeZoneName element
ms:assetid: b62c308c-147d-4099-956f-eb3b97379521
ms:mtpsurl: https://msdn.microsoft.com/library/Dn438965(v=office.15)
ms:contentKeyID: 57094004
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state/timeZoneName element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the name of the local time zone where the presence state is published.

```xml
<st:timeZoneName xmlns:st="http://schemas.microsoft.com/2006/09/sip/state" >xs:string</st:timeZoneName>
```

xs:string

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
<td><p><a href="state-category-instance-value-elements.md">state category instance value elements</a></p></td>
<td><p>An enhanced presence state category instance value with the specification of the time zone name.</p></td>
</tr>
</tbody>
</table>


## Text value

A time zone name string.

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

