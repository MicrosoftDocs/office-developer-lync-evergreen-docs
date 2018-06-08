---
title: contactCard/address/street element
TOCTitle: contactCard/address/street element
ms:assetid: 00b0853d-b5eb-484a-895b-25d28027c5e4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454724(v=office.15)
ms:contentKeyID: 57093421
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/address/street element


**Applies to:** Lync 2013 | Lync Server 2013

The street name of a contact’s address.

```xml
<street updated="DateTime" [anyAttr]="string" LCID="lcid">string</street>
```

LCIDType

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
<td><p>LCID</p></td>
<td><p>Optional attribute of the unsigned integer type indicating the locale ID for the locale-specific display of the string value of the element. When unspecified, the default locale is implied.</p></td>
</tr>
<tr class="even">
<td><p>updated</p></td>
<td><p>Optional attribute of the xs:dateTime type indicating the time when this element was last updated.</p></td>
</tr>
<tr class="odd">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name in any namespace</p></td>
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
<td><p><a href="contactcard-address-element.md">contactCard/address element</a></p></td>
<td><p>The address property of a contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

A locale-specific string value.

## Remarks

The type of this element is derived from LCIDType that is derived from updatedStringType that is further derived from the simple xs:string type. For more information, see the contactCard schema definition file (contactCard.xsd).

## Example

The following XML code snippet shows a contactCard category instance containing a contact’s work address.

``` 
  <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
    <address type="work">
      <street>123 Any Street</street>
      <city>Redmond</city>
      <state>WA</state>
      <zipcode>98223</zipcode>
      <countryCode>US</countryCode>
    </address>
    <url type="sharepoint">http://admin.contoso.com</url>
  </contactCard>
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
<td><p>http://schemas.microsoft.com/2006/09/sip/contactcard</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>contactCard</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>contactCard.xsd, contactCardTypes.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[contactCard category instance value element](contactcard-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

