---
title: alerts category instance value element
TOCTitle: alerts category instance value element
ms:assetid: 8bfc3f35-57e2-431a-8f99-d364ebb1c541
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454690(v=office.15)
ms:contentKeyID: 57093341
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# alerts category instance value element


_**Applies to:** Lync 2013 | Lync Server 2013_

Contains the roaming alerts options that can be set by the user on Microsoft Lync 2013.

``` xml
<alerts xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    majorVersion="xs:unsignedInt"
    minorVersion="xs:unsignedInt"
    [anyAttr]="any attribute" 
    xmlns="http://schemas.microsoft.com/2006/09/sip/options/alerts">
    <alertsWhenDoNotDisturb>alertsWhenDoNotDisturbEnumEx token</alertsWhenDoNotDisturb>
    <notifyAdditionToContactList>xs:boolean</notifyAdditionToContactList>
    <showMessageTextForIncomingConversation>xs:boolean</showMessageTextForIncomingConversation>
    <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <[any] >any element</[any]>
    <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[any] xmlns="any_namespace">any element</[any]>
    </extension>
</alerts>
```

alertsType

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
<td><p>Optional attribute to specify the major version number of this element.</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify the minor version number of this element.</p></td>
</tr>
<tr class="odd">
<td><p>anyAttr</p></td>
<td><p>Optional custom attribute of any name in any namespace.</p></td>
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
<td><p>alertsWhenDoNotDisturb</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple element containing a token of the altersWhenDoNotDisturbEnumEx type to set options on how the user gets notified when the user in the Do Not Disturb mode. Lync 2013 recognizes the following tokens:</p>
<dl>
<dt>displayAllAlerts</dt>
<dd><p>Display all alerts, except for conversation alerts, from people in the user's Workgroup container. This is the default token.</p>
</dd>
<dt>displayAlertsFromHighPresence</dt>
<dd><p>Display only conversation alerts from people in the user's Workgroup access level.</p>
</dd>
<dt>noAlerts</dt>
<dd><p>Do not display alerts.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>notifyAdditionToContactList</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple element containing a Boolean flag to specify whether the user gets notified when someone adds the user to his or her contact list (<em>true</em>) or not (<em>false</em>).</p>
<p>Lync 2013 adds the notifyAdditionToContactList element when the user selects (True) or clears (False) <strong>Notify me when someone adds me to his or her contact list</strong> from the <strong>Alerts</strong> option in the <strong>Lync Options</strong> dialog box. By default, Lync 2013 sets this value as True.</p></td>
</tr>
<tr class="odd">
<td><p>showMessageTextForIncomingConversation</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple element containing a Boolean flag to specify whether the user is shown the subject or message text in conversation alerts (<em>true</em>) or not (<em>false</em>).</p>
<p>Lync 2013 adds the <strong>showMessageTextForIncomingConversation</strong> element when the user selects (True) or clears (False) <strong>Display subject or message in conversation alerts</strong> from the <strong>Alerts</strong> option in the <strong>Lync Options</strong> dialog box. By default, Lync 2013 sets this value as True.</p></td>
</tr>
<tr class="even">
<td><p>ct:delimiter</p></td>
<td><p>0 or more</p></td>
<td><p>An empty element, of the CommonTypes (ct) namespace, to mark the start of a schema extension to its parent element. Elements describing the extension are enclosed between a ct:delimiter and ct:end elements or between two ct:delimiter elements.</p></td>
</tr>
<tr class="odd">
<td><p>ct:end</p></td>
<td><p>0 or 1</p></td>
<td><p>An empty element, of the CommonTypes (ct) namespace, to mark the end of all the schema extensions to its parent element.</p></td>
</tr>
<tr class="even">
<td><p>ct:extension</p></td>
<td><p>0 or more</p></td>
<td><p>An element, of the CommonTypes (ct) namespace, to hold any elements of any namespace as an application-defined custom extension to the parent element.</p></td>
</tr>
<tr class="odd">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>A custom element describing an extension to its parent element. When enclosed between a ct:delimiter element and a ct:end element or between two ct:delimiter elements, this element serves to describe a schema extension and can have any name in the namespace of its parent element. When contained in an ct:extension element, this element describes the application-defined custom extension and can have any name in any namespace.</p></td>
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
<td><p>This is a top-level element as the value of an enhanced presence data of the alerts category name.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

The options specified by this category instance correspond to the choices that can be set by a user from the **Alerts** option in the **Lync Options** dialog box.

The element supports schema extensions as well as custom extension and can have a custom attribute of any type.

## Example

The following code example sets the alerts from high presence

``` xml
<alerts xmlns="http://schemas.microsoft.com/2006/09/sip/options/alerts">
   <alertsWhenDoNotDisturb>displayAlertsFromHighPresence</alertsWhenDoNotDisturb>
   <notifyAdditionToContactList>true</notifyAdditionToContactList>
</alerts>
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
<td><p>http://schemas.microsoft.com/2006/09/sip/options/alerts</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>Options-Alerts</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>Options-Alerts.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Category instance elements for presence](category-instance-elements-for-presence.md)

#### Concepts

[Workgroup container](workgroup-container.md)

[Self container](self-container.md)

