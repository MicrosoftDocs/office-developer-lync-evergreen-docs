---
title: state/endpointLocation element
TOCTitle: state/endpointLocation element
ms:assetid: 8c896006-6c4f-4e62-b9b0-fbaf0df255f0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454804(v=office.15)
ms:contentKeyID: 57093897
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state/endpointLocation element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies the location of an endpoint.

``` xml
<st:endpointLocation xmlns:st="http://schemas.microsoft.com/2006/09/sip/state" >st:endpointLocationEnumEx</st:endpointLocation> 
```

st:endpointLocationEnumEx

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
<td><p>The presence state category instance value with a specification of the endpoint location.</p></td>
</tr>
</tbody>
</table>


## Text value

A token of the st:endpointLocationEnumEx type.

## Remarks

Microsoft Lync 2013 recognizes the following endpoint location tokens:

  - office  
    An office location.

  - mobile  
    A mobile location

  - home  
    A home location

  - none  
    Unspecified location

In addition, any other location string can also be specified.

## Example

The following XML snippet shows machine state category instance value containing a specification of the location information.

    <state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           manual="false" 
           xsi:type="machineState">
       <availability>3500</availability>
       <endpointLocation>Building 10, Room 101, West Campus</endpointLocation>
       <timeZoneBias>480</timeZoneBias>
       <timeZoneName>Pacific Standard Time</timeZoneName>
       <timeZoneAbbreviation>PST</timeZoneAbbreviation>
       <device>computer</device>
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

Presence State and state Category Instances

