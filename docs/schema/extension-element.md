---
title: extension element
TOCTitle: extension element
ms:assetid: 8f6bf992-33d2-43d1-9972-0ff7a796872d
ms:mtpsurl: https://msdn.microsoft.com/library/Dn438998(v=office.15)
ms:contentKeyID: 57094044
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# extension element


**Applies to:** Lync 2013 | Lync Server 2013

Contains custom elements of any name in any namespace as application-specific extension to the parent element defined in an enhanced presence schema.

```xml
<ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >
   <[any]>...</[any]>
</ct:extension>
```

xs:element

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

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
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>An XML element of any name in any namespace specifying custom extension to an enhanced presence schema.</p></td>
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
<td><p>Various</p></td>
<td><p>Element representing an enhanced presence category instance value and some of its child elements can support such an extension.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

Where it is defined in an enhanced presence schema, this element can be used to support application-specific custom extension of the elements. The child elements specifying the extension can be of any name and in any namespace.

## Example

```xml
<contactCard 
     xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" 
     xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >
  <identity>
    <name>
      <displayName>bob</displayName>
    </name>
    <email>bob@contoso.com</email>
  </identity>
  <address type="work" />
  <company>Contoso, LTD.</company>
  <title>SR. DEVELOPMENT LEAD</title>
  <office>A</office>
  <phone type="work">
    <uri>tel:+14255550150;ext=50150</uri>
  </phone>
  <ct:delimiter />
  <ringIm>true</ringIm>
  <ct:end />
  <ct:extension>
    <e:test xmlns:e="http://schemas.microsoft.com/2006/09/sip/ccextension" />
    <e:test2 xmlns:e="http://schemas.microsoft.com/2006/09/sip/ccextension" />
  </ct:extension>
</contactCard>
```

In the code snippet above, \<e:test\> and \<e:test2\> are two elements introduced as a custom extension to a contactCard category instance.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/commontypes</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>CommonTypes</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>CommonTypes.Xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Common elements for extension and customization](common-elements-for-extension-and-customization.md)

