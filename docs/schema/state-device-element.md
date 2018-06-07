---
title: state/device element
TOCTitle: state/device element
ms:assetid: d48a27ba-af85-49d9-9b95-ccfd490b093a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438959(v=office.15)
ms:contentKeyID: 57093993
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state/device element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the device type where the presence state is published.

``` xml
<st:device xmlns:st="http://schemas.microsoft.com/2006/09/sip/state" >st:deviceTypeEnumEx </st:device>
```

st:deviceTypeEnumEx

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
<td><p>An enhanced presence state category instance value with the specification of the device type.</p></td>
</tr>
</tbody>
</table>


## Text value

A device type token or string.

## Remarks

Microsoft Lync 2013 recognizes the following device type tokens:

  - computer  
    The device is a computer on which Lync 2013 is running.

  - deskphone  
    The device is a desk phone on which Lync Phone Edition is running.

  - mobile  
    The device is a mobile phone on which Microsoft Lync 2010 for Android, iPad, iPhone, Nokia, or Windows Phone is running.

  - web  
    This is a computer on which Microsoft Lync Web App is running.

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

Presence State and state Category Instances

