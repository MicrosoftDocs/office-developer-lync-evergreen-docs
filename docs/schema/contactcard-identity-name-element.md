---
title: contactCard/identity/name element
TOCTitle: contactCard/identity/name element
ms:assetid: 2b8bb29a-d463-4689-8df1-4cf73daf8c40
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454720(v=office.15)
ms:contentKeyID: 57093407
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/identity/name element


**Applies to:** Lync 2013 | Lync Server 2013

Contact’s name as part of the identity.

```xml
<name updated="DateTime" [[anyAttr]]="String">
    <displayName updated="DateTime" [anyAttr]="String" LCID="lcid">string</displayName>
    <extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[[any]] >custom element</[[any]]>
    </extension>
    <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</phone>
```

nameType

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
<td><p>Optional attribute to indicate when this name element was last updated.</p></td>
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
<td><p>displayName</p></td>
<td><p>0 or more</p></td>
<td><p>A locale-specific display name of the contact.</p></td>
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
<td><p><a href="contactcard-identity-element.md">contactCard/identity element</a></p></td>
<td><p>The identity of the contact represented by the contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

There can be at most one sequence of version-dependent schema extensions that are enclosed between one or more delimiter elements and an end element. Each delimiter element can be followed by zero or more of any elements.

## Example

The following XML code snippet shows a contactCard category instance containing the name and email address as the identity of a contact.

    <contactCard xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
        xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
        <identity>
          <name>
            <displayName>Bob</displayName>
          </name>
          <email>bob@contoso.com</email>
        </identity>
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

