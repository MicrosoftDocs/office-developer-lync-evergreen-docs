---
title: alerts/showMessageTextForIncomingConversation element
TOCTitle: alerts/showMessageTextForIncomingConversation element
ms:assetid: ace60d1b-5887-4d98-bc6c-64e448cbf7a5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454694(v=office.15)
ms:contentKeyID: 57093339
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# alerts/showMessageTextForIncomingConversation element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies whether to display the subject or message in conversation alerts.

[alerts category instance value element](alerts-category-instance-value-element.md)  
  showMessageTextForIncomingConversation Element  

```xml
<showMessageTextForIncomingConversation
   xmlns="http://schemas.microsoft.com/2006/09/sip/alerts">Boolean</showMessageTextForIncomingConversation>
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

Microsoft Lync 2013 publishes this element when the user selects **Display subject or message in conversation alerts** from the **Alerts** option in the **Lync Options** dialog box. By default, Lync 2013 sets this value to true.

## Example

The XML code snippet shows an alerts category instance value that indicates that the user will not be shown the subject or message text in conversation alerts.

    <alerts xmlns="http://schemas.microsoft.com/2006/09/sip/alerts">
        <showMessageTextForIncomingConversation>false</showMessageTextForIncomingConversation>
    </alerts>

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

