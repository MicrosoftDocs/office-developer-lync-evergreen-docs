---
title: contactCard/url element
TOCTitle: contactCard/url element
ms:assetid: 2f6d1b18-fa2d-4066-8f5c-02e1550e3e2b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454733(v=office.15)
ms:contentKeyID: 57093485
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/url element


_**Applies to:** Lync 2013 | Lync Server 2013_

The URL of the source where the contact information originates.

``` xml
<url type="urlTypeEnumEx" updated="dateTime" [anyAttr]="anyAttr">URL string</url>
```

urlType

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
<td><p>Attribute of the urlTypeEnumEx type to indicate the source where the contact information originates. Microsoft Lync 2013 recognizes the following URL type tokens:</p>
<dl>
<dt><em>sharepoint</em></dt>
<dd><p>The contact information originates from a SharePoint site.</p>
</dd>
<dt><em>voicemail</em></dt>
<dd><p>The contact information originates from Exchange Server.</p>
</dd>
<dt><em>photo</em></dt>
<dd><p>The contact information originates from the specified photo site.</p>
</dd>
<dt><em>other</em></dt>
<dd><p>The contact information originates from some other contact information source.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>updated</p></td>
<td><p>Optional attribute of the xs:dateTime type indicating the time when the office location was last updated.</p></td>
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

A URL string

## Remarks

The type of this element is derived from updatedAnyURIType that is derived from the xs:anyURI type. For more information, see the contactCard schema definition file (contactCard.xsd).

## Example

The following XML code snippet shows a contactCard category instance containing the source URL.

    <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" isUCEnabled="true">
       <url type="voicemail">sip:bob@contoso.com;opaque=app:voicemail;local-resource-path=voicememo</url>
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

