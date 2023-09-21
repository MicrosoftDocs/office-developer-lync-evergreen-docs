---
title: contactCard/identity element
TOCTitle: contactCard/identity element
ms:assetid: fe50adf7-014f-4c5a-bc5e-d3083c32e72a
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454719(v=office.15)
ms:contentKeyID: 57093406
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/identity element


**Applies to**: Lync Server 2013

The identity of the contact, including the display name and email address.

```xml
<identity updated="DateTime" [anyAttr]="String">
    <name updated="DateTime" [anyAttr]="String">
        <displayName updated="DateTime" [anyAttr]="String"
                LCID="lcid">Contact’s name</displayName>
        <[any] >custom element</[any]>
        <extension 
            xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
            <[any] >custom element</[any]>
        </extension>
        <delimiter 
          xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
        <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    </name>
    <email updated="DateTime" [anyAttr]="String">value</email>
    <extension 
        xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[any] >[any] element</[any]>
    </extension>
    <delimiter 
        xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</identity>
```

identityType

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
<td><p>The time when the identity information was last updated.</p></td>
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
<td><p>name</p></td>
<td><p>0 or 1</p></td>
<td><p>The contact’s name</p></td>
</tr>
<tr class="even">
<td><p>email</p></td>
<td><p>0 or more</p></td>
<td><p>The contact’s email address</p></td>
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

There can be at most one sequence of version-dependent schema extensions that are enclosed between one or more [delimiter element](delimiter-element.md) elements and an [end element](end-element.md) element. Each delimiter element can be followed by zero or more of any elements.

## Example

The following XML code snippet shows a contactCard category instance bearing the identity information of a contact named "bob".

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

In Microsoft Lync 2013 the [contactCard category instance value element](contactcard-category-instance-value-element.md) category instance bearing only the identity information has an instance Id of zero.

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

