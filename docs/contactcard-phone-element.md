---
title: contactCard/phone element
TOCTitle: contactCard/phone element
ms:assetid: 964f5b37-6545-411c-8b96-ec5b0effd161
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454716(v=office.15)
ms:contentKeyID: 57093403
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/phone element


_**Applies to:** Lync 2013 | Lync Server 2013_

Information about the contact’s phone, including the display name and email address.

``` xml
<phone updated="DateTime" [[anyAttr]]="String" type="phoneTypeToken">    <uri updated="DateTime" [anyAttr]="String">TEL URI string</uri>    <displayString updated="DateTime" [anyAttr]="String" LCID="lcid">string</displayString>    <extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">        <[[any]] >custom element</[[any]]>    </extension>    <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />    <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" /></phone>
```

phoneType

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
<td><p>The phone type of a phoneTypeTokenEx value. Microsoft Lync 2013 recognizes the following phone type tokens for this attribute:</p>
<dl>
<dt><em>work</em></dt>
<dd><p>This is a work phone.</p>
</dd>
<dt><em>home</em></dt>
<dd><p>This is a home phone.</p>
</dd>
<dt><em>mobile</em></dt>
<dd><p>This is a mobile phone.</p>
</dd>
<dt><em>other</em></dt>
<dd><p>This is some other phone.</p>
</dd>
<dt><em>custom1</em></dt>
<dd><p>This is a custom-defined phone.</p>
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
<td><p>uri</p></td>
<td><p>1</p></td>
<td><p>The TEL URI of the phone</p></td>
</tr>
<tr class="even">
<td><p>displayString</p></td>
<td><p>0 or more</p></td>
<td><p>A locale-specific display of the phone number.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A beginning marker to start a version-specific schema extension.</p></td>
</tr>
<tr class="even">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The ending marker to end all the schema extensions.</p></td>
</tr>
<tr class="odd">
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

The following XML code snippet shows a contactCard category instance containing a contact’s work phone information, in addition to the company name, professional title and office location.

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
<td><p>False</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[contactCard category instance value element](contactcard-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

