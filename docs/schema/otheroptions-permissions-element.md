---
title: otherOptions/permissions element
TOCTitle: otherOptions/permissions element
ms:assetid: 0d1925c4-072a-47ce-a824-5d25f0a616a5
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454756(v=office.15)
ms:contentKeyID: 57093643
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# otherOptions/permissions element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the permissions configuration in Microsoft Lync 2013.

```xml
<permissions xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns="http://schemas.microsoft.com/2006/09/sip/options/otherOptions">
    <personalInformationManager>personalInformationManagerEnumEx</personalInformationManager>
    <voiceMailLastAccessTimestamp>xs:string</voiceMailLastAccessTimestamp>
    <missedConversationLastAccessTimestamp>xs:string</missedConversationLastAccessTimestamp>
    <autoRetrievOofFromOutlook>xs:boolean</autoRetrieveOofFromOutlook>
    <publishCalendarPresence>xs:boolean</publishCalendarPresence>
    <imAutoArchving>xs:boolean</imAutoArchiving>
    <callLogAutoArchiving>xs:boolean</callLogAutoArchiving>
    <publishMeetingSubjectAndLocation>xs:boolean</publishMeetingsubjectAndLocation>
    <publishActivityHistory>xs:boolean</publishActivityHistory>
    <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <[any] xmlns="http://schemas.microsoft.com/2006/09/sip/options/otherOptions">any element for a schema extension</[any]>
    <ct:end/>
    <ct:extension>
        <[any] xmlns="any_namespace">any element for custom extension</[any]>
    </ct:extension>
</permissions>
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
<td><p><a href="otheroptions-permissions-personalinformationmanager-element.md">otherOptions/Permissions/personalInformationManager element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the personalInformationManagerEnumEx type to specify the personal information manager for the user.</p></td>
</tr>
<tr class="even">
<td><p><a href="otheroptions-permissions-autoretrieveooffromoutlook-element.md">otherOptions/Permissions/autoRetrieveOofFromOutlook element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the xs:boolean type to specify whether to automatically retrieve OOF messages from Outlook.</p></td>
</tr>
<tr class="odd">
<td><p>missedConversationLastAccessTimestamp</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the xs:string type to specify the time when the missed conversations were last accessed.</p></td>
</tr>
<tr class="even">
<td><p><a href="otheroptions-permissions-publishcalendarpresence-element.md">otherOptions/Permissions/publishCalendarPresence element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the xs:boolean type to specify whether to publish calendar presence (true) or not (false). The default setting is true.</p></td>
</tr>
<tr class="odd">
<td><p><a href="otheroptions-permissions-imautoarchiving-element.md">otherOptions/Permissions/imAutoArchiving element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the xs:boolean type to specify whether to automatically archive IM messages (true) or not (false). The default setting is true.</p></td>
</tr>
<tr class="even">
<td><p><a href="otheroptions-permissions-calllogautoarchiving-element.md">otherOptions/Permissions/callLogAutoArchiving element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the xs:boolean type to specify whether to automatically archive call logs (true) or not (false). The default setting is true.</p></td>
</tr>
<tr class="odd">
<td><p><a href="otheroptions-permissions-publishmeetingsubjectandlocation-element.md">otherOptions/permissions/publishMeetingSubjectAndLocation element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the xs:boolean type to specify whether to publish meeting subject and location (true) or not (false). The default setting is true.</p></td>
</tr>
<tr class="even">
<td><p>voiceMailLastAccessTimestamp</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the xs:string type to specify the time when the voice mail was last accessed.</p></td>
</tr>
<tr class="odd">
<td><p><a href="otheroptions-publishactivityhistory-element.md">otherOptions/publishActivityHistory element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element containing a value of the xs:boolean type to specify whether to publish activity history (true) or not (false). The default setting is true.</p></td>
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
<td><p><a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a></p></td>
<td><p>The otherOptions category instance value containing the permissions element.</p></td>
</tr>
</tbody>
</table>


## Text value

None

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

