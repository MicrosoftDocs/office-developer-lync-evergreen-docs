---
title: alerts/notifyAdditionToContactList element
TOCTitle: alerts/notifyAdditionToContactList element
ms:assetid: ed217ffd-5bb3-4502-b826-90af4153ab8d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454692(v=office.15)
ms:contentKeyID: 57093345
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# alerts/notifyAdditionToContactList element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies whether to display alerts to the user when someone adds the user to his or her contact list.

[alerts category instance value element](alerts-category-instance-value-element.md)  
  notifyAdditionToContactList Element  

```xml
<al:notifyAdditionToContactList
    xmlns:al="http://schemas.microsoft.com/2006/sip/alerts">boolean</al:notifyAdditionToContactList>
```

Boolean

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

True or False

## Remarks

Microsoft Lync 2013 publishes this element when the user selects **Notify me when someone adds me to his or her contact list** from the **Alerts** option in the **Lync Options** dialog box. By default, Lync 2013 sets this value as True.

## Example

The following XML code snippet shows an alerts category instance value indicating that the user will not be notified when someone adds the user to his or her contact list.

    <alerts xmlns="http://schemas.microsoft.com/2006/sip/alerts">
       <notifyAdditionToContactList>false</notifyAdditionToContactList>
    </alerts>

Insert content here.

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

