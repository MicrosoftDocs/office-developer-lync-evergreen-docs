---
title: Enhanced Presence category schemas
TOCTitle: Enhanced Presence category schemas
ms:assetid: b0126b0d-345e-4c30-b2b7-c33951b35039
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454624(v=office.15)
ms:contentKeyID: 57093014
ms.date: 02/11/2016
mtps_version: v=office.15
---

# Enhanced Presence category schemas


**Applies to:** Lync 2013 | Lync Server 2013

Installation of the Microsoft Unified Communications Enhanced Presence Schemas for Microsoft Lync Server 2013 package installs the following XML Schema Definition (XSD) files on your computer. The following table lists the XSD files, the names of the corresponding XSD types defining the associated presence categories, the names of the XML elements as instances of the corresponding categories, and the category names used in registration, publication, and subscription of the categories.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>XSD file name</p></th>
<th><p>Category XSD type (*)</p></th>
<th><p>Category instance data element (**)</p></th>
<th><p>Category name (***)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>calendarData.xsd</p></td>
<td><p>calendarDataType</p></td>
<td><p>&lt;<a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a>&gt;</p></td>
<td><p>calendarData</p></td>
</tr>
<tr class="even">
<td><p>contactCard.xsd</p></td>
<td><p>contactCardType</p></td>
<td><p>&lt;<a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a>&gt;</p></td>
<td><p>contactCard</p></td>
</tr>
<tr class="odd">
<td><p>device.xsd</p></td>
<td><p>deviceType</p></td>
<td><p>&lt;<a href="device-category-instance-value-element.md">device category instance value element</a>&gt;</p></td>
<td><p>device</p></td>
</tr>
<tr class="even">
<td><p>note.xsd</p></td>
<td><p>noteType</p></td>
<td><p>&lt;<a href="note-category-instance-value-element.md">note category instance value element</a>&gt;</p></td>
<td><p>note</p></td>
</tr>
<tr class="odd">
<td><p>options-Alerts.xsd</p></td>
<td><p>alertsType</p></td>
<td><p>&lt;<a href="alerts-category-instance-value-element.md">alerts category instance value element</a>&gt;</p></td>
<td><p>alerts</p></td>
</tr>
<tr class="even">
<td><p>options-OtherOptions.xsd</p></td>
<td><p>otherOptionsType</p></td>
<td><p>&lt;<a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a>&gt;</p></td>
<td><p>otherOptions</p></td>
</tr>
<tr class="odd">
<td><p>options-RccOptions.xsd</p></td>
<td><p>rccOptionsType</p></td>
<td><p>&lt;<a href="rccoptions-category-instance-value-element.md">rccOptions category instance value element</a>&gt;</p></td>
<td><p>rccOptions</p></td>
</tr>
<tr class="even">
<td><p>options-userInformation.xsd</p></td>
<td><p>userInformationType</p></td>
<td><p>&lt;<a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a>&gt;</p></td>
<td><p>userInformation</p></td>
</tr>
<tr class="odd">
<td><p>routing.xsd</p></td>
<td><p>routing-type</p></td>
<td><p>&lt;<a href="routing-category-instance-value-element.md">routing category instance value element</a>&gt;</p></td>
<td><p>routing</p></td>
</tr>
<tr class="even">
<td><p>publicationGrammarSchemaForNewPublicationManifest.xsd</p></td>
<td><p>categoryPublicationManifestType</p></td>
<td><p>&lt;<a href="categorypublicationmanifest-element.md">categoryPublicationManifest element</a>&gt;</p></td>
<td><p>Category publication grammar</p></td>
</tr>
<tr class="odd">
<td><p>service.xsd</p></td>
<td><p>servicesType</p></td>
<td><p>&lt;<a href="services-category-instance-value-element.md">services category instance value element</a>&gt;</p></td>
<td><p>services</p></td>
</tr>
<tr class="even">
<td><p>state.xsd</p></td>
<td><p>stateType</p>
<p>calendarState</p>
<p>phoneState</p>
<p>userState</p>
<p>machineState</p>
<p>aggregateState</p>
<p>aggregateMachineState</p></td>
<td><p>&lt;<a href="state-category-instance-value-elements.md">state category instance value elements</a>&gt;</p>
<p>&lt;<a href="state-element_3.md">state[@type='calendarState'] element</a>&gt;</p>
<p>&lt;<a href="state-element_1.md">state[@type='phoneState'] element</a>&gt;</p>
<p>&lt;<a href="state-element.md">state[@type='userState'] element</a>&gt;</p>
<p>&lt;<a href="state-element_2.md">state[@type='machineState'] element</a>&gt;</p>
<p>&lt;<a href="state-element_4.md">state[@type='aggregateState'] element</a>&gt;</p>
<p>&lt;<a href="state-element_5.md">state[@type='aggregateMachineState'] element</a>&gt;</p></td>
<td><p>state</p>
<p>state</p>
<p>state</p>
<p>state</p>
<p>state</p>
<p>state</p>
<p>state</p></td>
</tr>
<tr class="odd">
<td><p>userProperties.xsd</p></td>
<td><p>userPropertiesType</p></td>
<td><p>&lt;<a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a>&gt;</p></td>
<td><p>userProperties</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>(*) This column shows the name of the XSD types defining presence categories in the corresponding XSD files.</P>
> <P>(**) This column shows the names of the XML elements that are used to represent an instance of a specified presence category. These instances are the data format written in a log file when tracing is turned on.</P>
> <P>(***) This column shows the category names used for the initial registration of the corresponding categories and subsequent publication of or subscription to their instances.</P>



By default, the XSD files are located in the %programFiles%\\Microsoft Lync Server 2013\\Enhanced Presence Schemas\\Schemas directory.

For the protocol information about these categories, see \[MS-PRES\]: Presence Protocol Specification at [http://go.microsoft.com/fwlink/?LinkId=195873](http://go.microsoft.com/fwlink/?linkid=195873)

## See also

#### Reference

[Lync-defined Enhanced Presence category instance elements](lync-defined-enhanced-presence-category-instance-elements.md)

#### Concepts

[Enhanced Presence data](enhanced-presence-data.md)

#### Other resources

[\[MS-PRES\]: Presence Protocol Specification](http://go.microsoft.com/fwlink/?linkid=195873)

