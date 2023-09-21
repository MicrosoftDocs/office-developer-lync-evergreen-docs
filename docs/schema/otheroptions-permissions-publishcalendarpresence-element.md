---
title: otherOptions/Permissions/publishCalendarPresence element
TOCTitle: otherOptions/Permissions/publishCalendarPresence element
ms:assetid: 6fc824a4-8f97-4af7-8dbd-68e2160c52c3
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454773(v=office.15)
ms:contentKeyID: 57093660
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# otherOptions/Permissions/publishCalendarPresence element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies whether to publish presence data obtained from the underlying calendar store.

```xml
<oo:publishCalendarPresence 
     xmlns:oo="http://schemas.microsoft.com/2006/09/sip/options/otherOptions"
     >boolean</oo:publishCalendarPresence>
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
<td><p><a href="otheroptions-permissions-element.md">otherOptions/permissions element</a></p></td>
<td><p>The permissions property of an otherOptions category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

true or false.

## Remarks

By default, Microsoft Lync 2013 sets this to true.

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

