---
title: dndState category instance value element
TOCTitle: dndState category instance value element
ms:assetid: 330cdd5b-ccc7-4324-86b3-96ad236db04b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454780(v=office.15)
ms:contentKeyID: 57093666
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# dndState category instance value element


**Applies to:** Lync 2013 | Lync Server 2013

The dndState category instance is an empty [state\[@type='userState'\] element](state-element.md) category instance. Its presence indicates the Do Not Disturb (DND) state is in effect and incoming calls from any container members are blocked.

```xml
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xsi:type="userState" 
       manual="true" />
```

stateType

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
<td><p>xsi:type</p></td>
<td><p>Specify a type of state category instance. The value must be the &quot;userState&quot; string.</p></td>
</tr>
<tr class="even">
<td><p>manual</p></td>
<td><p>Specify that this publication is manual (&quot;true&quot;) or automatic (&quot;false&quot;).</p></td>
</tr>
</tbody>
</table>


#### Child elements

None

#### Parent elements

None

## Text value

None

## Remarks

This is a [state\[@type='userState'\] element](state-element.md) category instance with a registered category name of dndState. It is used as a Boolean flag to block incoming calls from any members of the container in which this category instance is published.

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

[state category instance value elements](state-category-instance-value-elements.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

