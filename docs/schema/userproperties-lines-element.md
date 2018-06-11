---
title: userProperties/lines element
TOCTitle: userProperties/lines element
ms:assetid: 4489d5ee-7ac3-4851-9ec4-06d62b3e6fc8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438970(v=office.15)
ms:contentKeyID: 57094015
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userProperties/lines element


**Applies to:** Lync 2013 | Lync Server 2013

Contains the description of the user controlled phones received via in-band provisioning from the server.

```xml
<up:lines xmlns:up="http://schemas.microsoft.com/2006/09/sip/categories" >
   <up:line>up:phoneLineType</up:line>
   ...
</up:lines>
```

xs:element

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
<td><p><a href="userproperties-lines-line-element.md">userProperties/lines/line element</a></p></td>
<td><p>0 or more</p></td>
<td><p>An element of the up:phoneLineType type describing a phone controlled by the user</p></td>
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
<td><p><a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a></p></td>
<td><p>The userProperties category instance value containing this list of phones.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

Microsoft Lync 2013 publishes the userProperties category instance to the Self container only.

## Example

The following XML snippet shows a userProperties category instance value.

```xml
<userProperties xmlns="http://schemas.microsoft.com/2006/09/sip/categories">
   <lines>
      <line lineType="Uc">tel:+1421112222;ext=12222</line>
   </lines>
   <telephonyMode>Uc</telephonyMode>
   <exumEnabled>1</exumEnabled>
   <exumURL>EUM:john@contoso.com;phone-context=EX-OCS-SIPSec.exchange.contoso.com</exumURL>
</userProperties>
```

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
<td><p>userProperties</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>userProperties.xsd</p></td>
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

[userProperties category instance value element](userproperties-category-instance-value-element.md)

#### Concepts

[Self container](self-container.md)

