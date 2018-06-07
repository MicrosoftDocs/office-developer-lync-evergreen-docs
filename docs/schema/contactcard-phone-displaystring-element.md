---
title: contactCard/phone/displayString element
TOCTitle: contactCard/phone/displayString element
ms:assetid: f5ca57aa-fa77-4bc3-b4f1-6e07972448e2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454747(v=office.15)
ms:contentKeyID: 57093634
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/phone/displayString element


**Applies to:** Lync 2013 | Lync Server 2013

The display of a phone number of a contact.

``` xml
<displayString updated="DateTime" [anyAttr]="String" LCID="lcid">string</displayString>
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
<td><p><a href="contactcard-phone-element.md">contactCard/phone element</a></p></td>
<td><p>The phone property of a contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

A locale-specific string value.

## Remarks

For more information about LCIDType, see the contactCard schema definition file (contactCard.xsd).

## Example

The following XML code snippet shows a contactCard category instance containing a contact’s work phone number.

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

