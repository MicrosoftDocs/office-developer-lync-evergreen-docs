---
title: contactCard/address element
TOCTitle: contactCard/address element
ms:assetid: 0cbca6bb-b3d8-4537-8a61-7dcf0e025bf4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454723(v=office.15)
ms:contentKeyID: 57093415
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/address element


**Applies to:** Lync 2013 | Lync Server 2013

The address of the contact.

```xml
<address type="addressTypeToken" [anyAttr]="string">
    <street updated="DateTime" [anyAttr]="string" LCID="lcid">string</street>
    <city updated="DateTime" [anyAttr]="string" LCID="lcid">string</city>
    <state updated="DateTime" [anyAttr]="string" LCID="lcid">string</state>
    <zipcode updated="DateTime" [anyAttr]="string" LCID="lcid">string</zipcode>
    <countryCode>string</countryCode>
    <[any] >any element</[any]>
    <extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[any] >any element</[any]>
    </extension>
    <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</address>
```

addressType

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
<td><p>type</p></td>
<td><p>The address type of an addressTypeTokenEx value. Microsoft Lync 2013 recognizes the following address type tokens for this attribute:</p>
<dl>
<dt><em>work</em></dt>
<dd><p>The address is a work address.</p>
</dd>
<dt><em>home</em></dt>
<dd><p>The address is a home address.</p>
</dd>
<dt><em>other</em></dt>
<dd><p>The address is some other address than work or home address.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>[anyAttr]</p></td>
<td><p>Custom attribute of any name in any namespace</p></td>
</tr>
</tbody>
</table>


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
<td><p>street</p></td>
<td><p>0 or more</p></td>
<td><p>The street name of the contact’s address</p></td>
</tr>
<tr class="even">
<td><p>city</p></td>
<td><p>0 or more</p></td>
<td><p>The city of the contact’s address</p></td>
</tr>
<tr class="odd">
<td><p>state</p></td>
<td><p>0 or more</p></td>
<td><p>The state or province name of the contact’s address.</p></td>
</tr>
<tr class="even">
<td><p>zipcode</p></td>
<td><p>0 or more</p></td>
<td><p>The zip/postal code of the contact’s address.</p></td>
</tr>
<tr class="odd">
<td><p>countryCode</p></td>
<td><p>0 or 1</p></td>
<td><p>The country code of the contact’s address.</p></td>
</tr>
<tr class="even">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A beginning marker to start a version-specific schema extension.</p></td>
</tr>
<tr class="odd">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The ending marker to end all the schema extensions.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-specific custom extension to this identity element.</p></td>
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
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>A contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

There can be at most one sequence of version-dependent schema extensions that are enclosed between one or more delimiter elements and an end element. Each delimiter element can be followed by zero or more of any elements.

## Example

The following XML code snippet shows a contactCard category instance containing the work address of a contact named "bob".

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

