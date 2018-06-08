---
title: otherOptions/publishActivityHistory element
TOCTitle: otherOptions/publishActivityHistory element
ms:assetid: 5a78c52a-7f62-4ec7-9e3d-c9e7977f1baf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454767(v=office.15)
ms:contentKeyID: 57093654
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# otherOptions/publishActivityHistory element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies whether to publish the activity history.

```xml
<oo:publishActivityHistory 
     xmlns:oo="http://schemas.microsoft.com/2006/09/sip/options/otherOptions"
     >boolean</oo:publishActivityHistory>
```

xs:boolean

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
<td><p><a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a></p></td>
<td><p>An otherOptions category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

true or false.

## Example

The following XML code snippet shows an otherOptions category instance containing a specification of the permissions:

```xml
  <otherOptions xmlns="http://schemas.microsoft.com/2006/09/sip/options/otherOptions">
    <permissions>
      <personalInformationManager>outlook</personalInformationManager>
      <autoRetrieveOofFromOutlook>true</autoRetrieveOofFromOutlook>
      <publishCalendarPresence>true</publishCalendarPresence>
      <imAutoArchiving>false</imAutoArchiving>
      <callLogAutoArchiving>true</callLogAutoArchiving>
      <publishMeetingSubjectAndLocation>true</publishMeetingSubjectAndLocation>
      <publishActivityHistory>false</publishActivityHistory>
      <voiceMailLastAccessTimestamp>123444332</voiceMailLastAccessTimestamp>
      <missedConversationLastAccessTimestamp>230405223</missedConversationLastAccessTimestamp>
    </permissions>
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
<td><p>http://schemas.microsoft.com/2006/09/sip/options/otherOptions</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>options-otherOptions</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>options-otherOptions.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[otherOptions category instance value element](otheroptions-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

