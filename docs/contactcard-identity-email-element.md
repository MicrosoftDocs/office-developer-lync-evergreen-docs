---
title: contactCard/identity/email element
TOCTitle: contactCard/identity/email element
ms:assetid: d97e2425-fa81-4d6c-9ba9-1d5c8c6c7d5f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454722(v=office.15)
ms:contentKeyID: 57093412
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/identity/email element


_**Applies to:** Lync 2013 | Lync Server 2013_

The email address as part a contact’s identity.

``` xml
<email updated="DateTime" [anyAttr]="String">value</email>
```

updatedAnyURIType

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
<td><p>Optional attribute of the xs:dateTime type indicating the when the email address was last updated.</p></td>
</tr>
<tr class="even">
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
<td><p><a href="contactcard-identity-element.md">contactCard/identity element</a></p></td>
<td><p>A contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

A SMTP address

## Remarks

The type of this element is derived from updatedAnyURIType that is derived from the xs:anyURI type. For more information, see the contactCard schema definition file (contactCard.xsd).

## Example

The following XML code snippet shows a contactCard category instance containing the name and email address as the identity of a contact.

    <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
      <identity>
        <name>
          <displayName>administrator</displayName>
        </name>
        <email>administrator@contoso.com</email>
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

