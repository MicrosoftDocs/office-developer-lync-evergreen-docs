---
title: contactCard/company element
TOCTitle: contactCard/company element
ms:assetid: 9222efc3-a0dc-4fe9-b6bb-920467a66b10
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454715(v=office.15)
ms:contentKeyID: 57093402
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/company element


**Applies to:** Lync 2013 | Lync Server 2013

The company name of the contact.

```xml
<company>locale-specifiable string</company>
```

Locale-specifiable string

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
<td><p>Optional attribute of the unsigned integer type indicating the locale ID for the locale-specific display of the company name.</p></td>
</tr>
<tr class="even">
<td><p>updated</p></td>
<td><p>Optional attribute of the xs:dateTime type indicating the time when the company name was last updated.</p></td>
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
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>A contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

A locale-specifiable string that can have its last update tracked.

## Remarks

The type of this element is derived from LCIDType that is derived from updatedStringType that is further derived from the simple xs:string type. For more information, see the contactCard schema definition file (contactCard.xsd).

## Example

The following XML code snippet shows a contactCard category instance containing a contact’s company name, in addition to the work phone, professional title and office location.

    <contactCard xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
        xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
        <company>CONTOSO</company>
        <title>TECHNICAL SUPPORT ENGINEER</title>
        <office>7/6302</office>
        <phone type="work">
           <uri>tel:+14251112222;ext=12222</uri>
           <displayString>+1 (425) 1112222 X12222</displayString>
        </phone>
    </contactCard>

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

