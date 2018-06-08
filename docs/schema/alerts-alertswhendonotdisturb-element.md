---
title: alerts/alertsWhenDoNotDisturb element
TOCTitle: alerts/alertsWhenDoNotDisturb element
ms:assetid: 7613bd15-e0c1-45a9-8133-77e06ee1bc58
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454691(v=office.15)
ms:contentKeyID: 57093342
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# alerts/alertsWhenDoNotDisturb element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies how to display alerts when the user is in the Do Not Disturb state.

[alerts category instance value element](alerts-category-instance-value-element.md)  
  alertsWhenDoNotDisturb Element  

```xml
<al:alertsWhenDoNotDisturb 
    xmlns:al="http://schemas.microsoft.com/2006/09/sip/alerts">
   token
</al:alertsWhenDoNotDisturb>
```

alertsWhenDoNotDisturbEnumEx

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
<td><p><a href="alerts-category-instance-value-element.md">alerts category instance value element</a></p></td>
<td><p>An alerts category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

The content of this element is an XML token. Microsoft Lync 2013 recognizes the following values as enumerated in the alertsWhenDoNotDisturbEnum type:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Token</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>displayAllAlerts</p></td>
<td><p>Display all alerts, except for conversation alerts, from people in the user's Workgroup container. This is the default value.</p></td>
</tr>
<tr class="even">
<td><p>displayAlertsFromHighPresence.</p></td>
<td><p>Display only conversation alerts from people in the user's Workgroup access level.</p></td>
</tr>
<tr class="odd">
<td><p>noAlerts</p></td>
<td><p>Do not display alerts.</p></td>
</tr>
</tbody>
</table>


## Example

The following XML code snippet shows an alerts category instance value that sets the alerts notification to display only conversation alerts from the user's team members, who have been granted the Workgroup access level.

    <?xml version="1.0" encoding="utf-8" ?>
    <al:alerts xmlns:al="http://schemas.microsoft.com/2006/09/sip/options/alerts">
         <al:alertsWhenDoNotDisturb>displayAlertsFromHighPresence</al:alertsWhenDoNotDisturb>
    </al:alerts>

In Lync 2013, a contact is granted a Workgroup access level if the contact is a member of Container 300, also known as the Workgroup container.

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
<td><p>False</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[alerts category instance value element](alerts-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

