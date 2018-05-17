---
title: contactCard category instance value element
TOCTitle: contactCard category instance value element
ms:assetid: 8ce4bdcf-6e3b-4b83-9e6e-7d50181cad94
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454726(v=office.15)
ms:contentKeyID: 57093426
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard category instance value element


_**Applies to:** Lync 2013 | Lync Server 2013_

Contains the contact information stored the underlying Active Directory.

``` xml
<contactCard xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard"
    updated="xs:dateTime"
    [anyAttr]="any "
    isUCEnabled="boolean"
    majorVersion="xs:unsignedInt"
    minorVersion="xs:unsignedInt">
    <identity updated="xs:dateTime" [anyAttr]="any">......</identity>
    <address type="addressTypeEnumEx" [anyAttr]="any"> ...... </address>
    <company updated="xs:dateTime" [anyAttr]="any" LCID="xs:unsignedInt">string</company>
    <department updated="DateTime" [anyAttr]="any" LCID="xs:unsignedInt">string</department>
    <title updated="xs:dateTime" [anyAttr]="any" LCID="xs:unsignedInt">string</title>
    <office updated="xs:dateTime" [anyAttr]="any" LCID="xs:unsignedInt">string</office>
    <url updated="xs:dateTime" [anyAttr]="any" type="urlTypeTokenEx">string</url>
    <phone updated="xs:dateTime" [anyAttr]="any" type="phoneTypeEnumEx">......</pone>
    <automaton>boolean</automaton>
    <type>presnetityTypeEnumEx</type>
    <description>xs:string of at most 1020 characters long</description>
    <displayADPhoto>boolean</displayADPhoto>
    <photo updated="xs:dateTime" [anyAttr]="any" type="photoTypeEnumEx">......</photo>
    <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <[any]>any element in the contactCard namespace</[any]>
    <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[any] xmlns="any namespace">custom element</[any]>
    </ct:extension>
</contactCard>
```

contactCardType

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
<td><p>updated</p></td>
<td><p>Optional attribute to indicate the date and time, of the 0001-01-01T00:00:00 format, when this <strong>contactCard</strong> instance was last updated.</p></td>
</tr>
<tr class="even">
<td><p>isUcEnabled</p></td>
<td><p>Optional attribute containing a Boolean flag to indicate if the Exchange Unified Messaging is enabled for this contact (true) or not (false).</p></td>
</tr>
<tr class="odd">
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent major version information of this contactCard element</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent minor version information of this contactCard element</p></td>
</tr>
<tr class="odd">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name in any namespace</p></td>
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
<td><p><strong>identity</strong></p></td>
<td><p>0 or more</p></td>
<td><p>The identity of the contact, including the display name and email address.</p></td>
</tr>
<tr class="even">
<td><p><strong>address</strong></p></td>
<td><p>0 or more</p></td>
<td><p>The address of the contact.</p></td>
</tr>
<tr class="odd">
<td><p><strong>company</strong></p></td>
<td><p>0 or more</p></td>
<td><p>The company name of the contact.</p></td>
</tr>
<tr class="even">
<td><p><strong>department</strong></p></td>
<td><p>0 or more</p></td>
<td><p>The department name of the contact.</p></td>
</tr>
<tr class="odd">
<td><p><strong>title</strong></p></td>
<td><p>0 or more</p></td>
<td><p>The professional title of the contact.</p></td>
</tr>
<tr class="even">
<td><p><strong>office</strong></p></td>
<td><p>0 or more</p></td>
<td><p>The office location of the contact.</p></td>
</tr>
<tr class="odd">
<td><p><strong>url</strong></p></td>
<td><p>0 or more</p></td>
<td><p>The URL of the source where the encapsulated contact information is obtained.</p></td>
</tr>
<tr class="even">
<td><p><strong>phone</strong></p></td>
<td><p>0 or more</p></td>
<td><p>Information about the contact’s phone.</p></td>
</tr>
<tr class="odd">
<td><p><strong>automaton</strong></p></td>
<td><p>0 or 1</p></td>
<td><p>A Boolean flag indicating if the contact is a not person (true) or a person (false).</p></td>
</tr>
<tr class="even">
<td><p><strong>type</strong></p></td>
<td><p>0 or 1</p></td>
<td><p>Introduced in the Office Communications Server 2007 release, this element specifies the type of the contact.</p></td>
</tr>
<tr class="odd">
<td><p><strong>description</strong></p></td>
<td><p>0 or 1</p></td>
<td><p>The description about the contact.</p>
<p>This is a schema extension introduced in the Office Communications Server 2007 R2 Release.</p></td>
</tr>
<tr class="even">
<td><p><strong>displayADPhoto</strong></p></td>
<td><p>0 or 1</p></td>
<td><p>A Boolean flag indicating if the contact’s photo stored in Active Directory is to displayed (true) or not (false).</p>
<p>This element is a schema extension introduced in the Microsoft Lync Server 2010 release.</p></td>
</tr>
<tr class="odd">
<td><p><strong>photo</strong></p></td>
<td><p>0 or more</p></td>
<td><p>A schema extension introduced in the Lync Server 2010 release to specify the location of user-specified photo of the contact.</p></td>
</tr>
<tr class="even">
<td><p><strong>[any]</strong></p></td>
<td><p>0 or more</p></td>
<td><p>Custom element in the same target namespace describing a schema extension.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A demarcation to separate version-dependent extensions.</p></td>
</tr>
<tr class="even">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The demarcation of the end of all the schema versions</p></td>
</tr>
<tr class="odd">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A version-dependent schema extension</p></td>
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
<td><p>None</p></td>
<td><p>This is a top-level element as an enhanced presence category instance</p></td>
</tr>
</tbody>
</table>


## Text value

This element does have any text value.

## Remarks

Multiple instances of **contactCard** can be used to publish different pieces of the contact information.

## Example

The following XML code snippet shows a contactCard category instance containing only the identity of the contact.

``` 
        <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
          <identity>
            <name>
              <displayName>bob</displayName>
            </name>
            <email>bob@contoso.com</email>
          </identity>
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

[Category instance elements for presence](category-instance-elements-for-presence.md)

