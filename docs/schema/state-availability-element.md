---
title: state/availability element
TOCTitle: state/availability element
ms:assetid: 01e355b5-6888-45be-8506-8c04089c91f1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438967(v=office.15)
ms:contentKeyID: 57094010
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
description: Learn about the state/availability element in Lync 2013 on Microsoft's official site. Understand availability status numbers and their meanings.
---

# state/availability element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies an availability number to indicate the presentity’s availability status.

```xml
<st:availability xmlns:st="http://schemas.microsoft.com/2006/09/sip/state">xs:unsignedInt</st:availability>
```

xs:unsignedInt

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
<td><p><a href="state-category-instance-value-elements.md">state category instance value elements</a></p></td>
<td><p>A presence state category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

An unsigned integer.

## Remarks

Microsoft Lync 2013 uses the following availability ranges:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Availability Number Ranges</p></th>
<th><p>Stabdard Availability Status</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0-4499</p></td>
<td><p>Available</p></td>
</tr>
<tr class="even">
<td><p>4500-5999</p></td>
<td><p>Available-Idle</p></td>
</tr>
<tr class="odd">
<td><p>6000-7499</p></td>
<td><p>Busy</p></td>
</tr>
<tr class="even">
<td><p>7500-8999</p></td>
<td><p>Busy-Idle</p></td>
</tr>
<tr class="odd">
<td><p>9000-11999</p></td>
<td><p>Do Not Disturb</p></td>
</tr>
<tr class="even">
<td><p>12000-14999</p></td>
<td><p>Be Right Back</p></td>
</tr>
<tr class="odd">
<td><p>15000-17999</p></td>
<td><p>Away</p></td>
</tr>
<tr class="even">
<td><p>18000 and higher</p></td>
<td><p>Offline</p></td>
</tr>
</tbody>
</table>


## Example

The following XML example shows a userState category instance value containing an availability number of 15500 to indicate the Out of Office status and a custom activity string of "Out of office until next week".

    <state xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xsi:type="userState"
            xmlns="http://schemas.microsoft.com/2006/09/sip/state">
       <availability>15500</availability>
       <activity>
          <custom LCID="1033">Out of office until next week</custom>
       </activity>
    </state>

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/state</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>state</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>state.xsd, statetypes.xsd</p></td>
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

[state category instance value elements](state-category-instance-value-elements.md)

#### Other resources

Presence State and state Category Instance

