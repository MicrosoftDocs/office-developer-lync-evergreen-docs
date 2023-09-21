﻿---
title: contactCard/address/countrycode element
TOCTitle: contactCard/address/countrycode element
ms:assetid: e67f2de7-0ced-4fe7-b628-8bd33c0b8f10
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454711(v=office.15)
ms:contentKeyID: 57093398
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/address/countrycode element


**Applies to:** Lync 2013 | Lync Server 2013

The country code in a contact’s address.

```xml
<countryCode>country code token</countryCode>
```

token

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
<td><p><a href="contactcard-address-element.md">contactCard/address element</a></p></td>
<td><p>The address property of a contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

A country code token.

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

