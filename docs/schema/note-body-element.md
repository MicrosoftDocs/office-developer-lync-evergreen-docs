---
title: note/body element
TOCTitle: note/body element
ms:assetid: c85fb20f-9edb-424c-9cee-fd5b9f4cffda
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454763(v=office.15)
ms:contentKeyID: 57093650
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# note/body element


**Applies to:** Lync 2013 | Lync Server 2013

Holds a personal or Out of Office message as a presence note.

``` xml
<body xmlns="http://schemas.microsoft.com/2006/09/sip/note"
      uri="uri"
      type="noteTypeEnumEx" 
      LCID="int >= 0" 
      startTime="xs:dateTime"
      endTime="xs:dateTime"
      [anyAttr]="anyattr">message string</body>
```

xs:anySimpleType

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
<td><p>Required attribute to specify the type of the presence note. Microsoft Lync 2013 recognizes the following type tokens as the value of this attribute:</p>
<dl>
<dt>personal</dt>
<dd><p>User-settable personal message.</p>
</dd>
<dt>OOF</dt>
<dd><p>Out of Office message set in Outlook.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>LCID</p></td>
<td><p>Optional attribute to specify locale ID of the string value.</p></td>
</tr>
<tr class="odd">
<td><p>uri</p></td>
<td><p>Optional attribute to specify the SIP URI of the note publisher.</p></td>
</tr>
<tr class="even">
<td><p>startTime</p></td>
<td><p>Optional attribute to specify the starting time of this note publication in a time-bound publication.</p></td>
</tr>
<tr class="odd">
<td><p>endTime</p></td>
<td><p>Optional attribute to specify the ending time of this note publication in a time-bound publication.</p></td>
</tr>
<tr class="even">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace</p></td>
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
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>The presence note category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

An instance of any XML simple type.

## Example

The following XML code snippet shows a presence note of the personal type.

    <nt:note xmlns:nt="http://schemas.microsoft.com/2006/09/sip/note">
       <nt:body type="personal">I'm away today.</nt:body>
    </nt:note>

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

[calendarData category instance value element](calendardata-category-instance-value-element.md)

[note category instance value element](note-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

