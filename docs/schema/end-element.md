---
title: end element
TOCTitle: end element
ms:assetid: fa2017e5-b3d8-4606-8262-909327de5cfb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439015(v=office.15)
ms:contentKeyID: 57094058
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# end element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the marker to end all the schema extensions.

```xml
<ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
<tns:[any]>...</tns:[any]>
<ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
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

This element serves to end all the schema extensions to its parent element. For each parent element, there can be at most one occurrence of this ct:end element even if multiple instances of ct:delimiter are present in the scenarios of multiple schema extension.

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

