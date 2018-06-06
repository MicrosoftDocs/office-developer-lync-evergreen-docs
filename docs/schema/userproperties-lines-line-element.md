---
title: userProperties/lines/line element
TOCTitle: userProperties/lines/line element
ms:assetid: 55ad992d-6e3e-4be2-a4bc-6fdfcc1ced66
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438972(v=office.15)
ms:contentKeyID: 57094017
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userProperties/lines/line element


_**Applies to:** Lync 2013 | Lync Server 2013_

Contains the description of a phone line controlled by the user.

``` xml
<up:line xmlns:up="http://schemas.microsoft.com/2006/09/sip/categories" 
       lineType="up:lineTypeEnumEx" 
       lineServer="xs:token"
       [anyAttri]="anyAttribute">xs:string</up:line>
```

phoneLineType

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
<td><p>lineType</p></td>
<td><p>Required attribute holding a token of the up:lineTypeEnumEx type to specify the type of the phone line controlled by the user. Microsoft Lync 2013 recognizes the following tokens: &quot;Uc&quot;, &quot;Rcc&quot; and &quot;Dual&quot;.</p></td>
</tr>
<tr class="even">
<td><p>lineServer</p></td>
<td><p>Holds a token of the xs:token type to specify the URI of the line server controlling a RCC phone. An example is &quot;tel:+14252223333&quot;.</p></td>
</tr>
<tr class="odd">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace.</p></td>
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
<td><p><a href="userproperties-lines-element.md">userProperties/lines element</a></p></td>
<td><p>The list of the user-controlled phone lines containing this phone.</p></td>
</tr>
</tbody>
</table>


## Text value

TEL URI of the phone line.

## Example

``` xml
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

