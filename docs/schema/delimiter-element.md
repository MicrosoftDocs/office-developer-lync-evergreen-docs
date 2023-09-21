---
title: delimiter element
TOCTitle: delimiter element
ms:assetid: 0b8e3cf1-3e5f-4700-bd64-f8a413a4ab22
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439012(v=office.15)
ms:contentKeyID: 57094055
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# delimiter element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies a marker to begin a schema extension for forward and backward compatibility.

```xml
<ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
<tns:[any]>...</tns:[any]>
<ct:end/>
```

xs:element

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

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
<td><p>Various</p></td>
<td><p>Element representing an enhanced presence category instance value and some of its child elements can support such an extension.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

This element serves as the beginning marker of a version-dependent schema extension to a parent element. A single extension is expressed by one or more other data elements, of any name in the same target namespace (tns:) of a given schema file, enclosed between this element and a \<ct:end\> element. This is illustrated in the following XML snippet, where \<tns:someElement\> represents a schema extension.

    <ct:delimiter />
    <tns:someElement>someValue</tns:someElement>
    <ct:end />

For multiple extensions to the same parent element, there will be multiple instances of the \<ct:delimiter/\> element, but a single occurrence of the \<ct:end/\> element. Each \<ct:delimiter/\> signifies the beginning of one version of the schema extension. All the versions of schema extension must be enclosed between the first \<ct:delimiter/\>element and an \<ct:end/\> element. This is illustrated in the following XML snippet, where \<tns:someOtherElement\> and \<tns:someOtherOtherElement\> represents another version of the extension.

    <ct:delimiter />
    <tns:someElement>someValue</tns:someElement>
    <ct:delimiter />
    <tns:someOtherElement>someOtherValue</tns:someOtherElement>
    <tns:someOtherOtherElement>someOtherOtherValue</tns:someOtherOtherElement>
    <ct:end />

## Example

The following XML snippet shows a use of the ct:delimiter and ct:end elementd to add a voiceMailStamp as a schema extension to the otherOptions category instance value.

```xml
<otherOptions xmlns="http://schemas.microsoft.com/2006/09/sip/options/otherOptions" xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes">
  <permissions>
    <personalInformationManager>outlook</personalInformationManager>
    <autoRetrieveOofFromOutlook>true</autoRetrieveOofFromOutlook>
    <publishCalendarPresence>true</publishCalendarPresence>
    <imAutoArchiving>true</imAutoArchiving>
    <callLogAutoArchiving>true</callLogAutoArchiving>
    <publishMeetingSubjectAndLocation>true</publishMeetingSubjectAndLocation>
  </permissions>
    
  <ct:delimiter/>
    <voiceMailTimestamp>2010-01-01T00:10:10</voiceMailTimestamp>
  <ct:end/>
</otherOptions>
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

