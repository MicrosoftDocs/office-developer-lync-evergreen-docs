---
title: noteHistory category instance value element
TOCTitle: noteHistory category instance value element
ms:assetid: f72179d7-f2de-4f87-a9a7-a8b89a75b2c3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454764(v=office.15)
ms:contentKeyID: 57093651
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# noteHistory category instance value element


_**Applies to:** Lync 2013 | Lync Server 2013_

Holds a previously published [note category instance value element](note-category-instance-value-element.md) category instance. A noteHistory category instance is a note category instance having the registered category name of noteHistory.

``` xml
<note xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    majorVersion="xs:unsignedInt"
    minorVersion="xs:unsignedInt"
    anyAttr="any" 
    xmlns="http://schemas.microsoft.com/2006/09/sip/note">
    <body uri="xs:anyURI"
          type="noteTypeEnumEx" 
          LCID="xs:unsignedInt" 
          startTime="xs:dateTime"
          endTime="xs:dateTime"
          [anyAttr]="anyattr">string value</body>
    <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <any xmlns="any">any element</any>
    </ct:extension>
    <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <[any]>any element in the note namespace</any>
    <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</device>
```

noteType

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
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent major version information.</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent minor version information.</p></td>
</tr>
<tr class="odd">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace</p></td>
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
<td><p>body</p></td>
<td><p>1 ore more</p></td>
<td><p>Message body of the presence note.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-dependent custom extension to this element.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A marker to begin a version-dependent schema extension.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Custom element of any name in the same namespace describing a schema extension to this element. This element must be enclosed between a delimiter element and an end element or between a two delimiter elements.</p></td>
</tr>
<tr class="odd">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The marker to end all the schema extensions.</p></td>
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

The same as with [note category instance value element](note-category-instance-value-element.md).

## Remarks

noteHistory category instances are published by a client and used to log the last N occurrences of the [note category instance value element](note-category-instance-value-element.md) publications for display in activity feeds. The value N is set by the server administrator as part of the presence policies and is provisioned to clients via in-band provisioning. The default value of N is 5.

Microsoft Lync 2013 publishes a null instance of noteHistory category to Container 100 and 32000 and it publishes non null noteHistory category instances to Container 200, 300 and 400.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/note</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>note</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>note.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[note category instance value element](note-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

