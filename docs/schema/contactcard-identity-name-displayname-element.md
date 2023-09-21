---
title: contactCard/identity/name/displayName element
TOCTitle: contactCard/identity/name/displayName element
ms:assetid: fd65cbd2-afbe-4c9c-a33b-55547859e72e
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454721(v=office.15)
ms:contentKeyID: 57093409
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/identity/name/displayName element


**Applies to:** Lync 2013 | Lync Server 2013

The display name of the contact.

```xml
<displayName updated="DateTime" [anyAttr]="String"
    LCID="lcid">string</displayName>
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
<td><p>Optional attribute of the unsigned integer type indicating the locale ID for the locale-specific display of the display name.</p></td>
</tr>
<tr class="even">
<td><p>updated</p></td>
<td><p>Optional attribute of the xs:dateTime type indicating the time when the display name was last updated.</p></td>
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
<td><p><a href="contactcard-identity-name-element.md">contactCard/identity/name element</a></p></td>
<td><p>A contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

A display name string.

## Remarks

This element is of the LCIDType type that is derived from updatedStringType that is further derived from the simple xs:string type. For more information, see the contactCard schema definition file (contactCard.xsd).

## Example

The following XML code snippet shows a contactCard category instance containing a contact’s company name, in addition to the work phone, professional title and office location.

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

[contactCard category instance value element](contactcard-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

