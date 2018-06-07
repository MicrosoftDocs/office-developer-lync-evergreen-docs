---
title: routing/preamble element
TOCTitle: routing/preamble element
ms:assetid: a552026b-a059-48dc-9d4d-3fbecc66cc46
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454775(v=office.15)
ms:contentKeyID: 57093663
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# routing/preamble element


**Applies to:** Lync 2013 | Lync Server 2013

Contains specific routing rules to forward incoming calls.

``` xml
<ro:preamble xmlns:ro="http://schemas.microsoft.com/2006/09/sip/routing">
    <ro:flags>...</ro:flags>
    <ro:wait>...</ro:wait>
    <ro:list>...</ro:list>
</ro:preamble>
```

ro:preamble-type

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
<td><p><a href="routing-preamble-flags-element.md">routing/preamble/flags element</a></p></td>
<td><p>0 or more</p></td>
<td><p>Specifies the names of routing rules.</p></td>
</tr>
<tr class="even">
<td><p><a href="routing-preamble-list-element.md">routing/preamble/list element</a></p></td>
<td><p>0 or more</p></td>
<td><p>Specifies the targets to which incoming calls are routed according to the specified policy.</p></td>
</tr>
<tr class="odd">
<td><p><a href="routing-preamble-wait-element.md">routing/preamble/wait element</a></p></td>
<td><p>0 or more</p></td>
<td><p>Specifies the time period in which the specified routing rules are applied before the calls are forwarded to the voicemail of the called party.</p></td>
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
<td><p><a href="routing-category-instance-value-element.md">routing category instance value element</a></p></td>
<td><p>The value of a routing category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

Microsoft Lync 2013 publishes a routing category instance to a container to enact the specified call forwarding policy on the incoming calls made by any members of the container. Unlike the publications of other presence category instances, the container members will not receive such publications of the routing category instance in subscription or query.

## Example

The following XML code snippet shows a routing rule that simultaneously ring another number when an incoming call is received.

    <routing xmlns="http://schemas.microsoft.com/02/2006/sip/routing" 
             name="rtcdefault" version="2" minSupportedClientVersion="2.0.0.0">
        <preamble>
           <flags name="clientflags" value="simultaneous_ring work_hours"/>
           <wait name="total" seconds="30"></wait>
           <list name="simultaneous_ring">
              <target uri="sip:+12223334444@contoso.com;user=phone"></target>
           </list>
        </preamble>
    </routing>

The \<flags\> element specifies the action (simultaneous\_ring) to be taken during the callee’s working-hours period (work\_hours). The target of the forwarded call is listed under the \<list\> element. The \<wait\> element specifies the time duration the ringing will last before the call is forwarded to the voicemail.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/routing</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>routing</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>routing.xsd</p></td>
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

[routing category instance value element](routing-category-instance-value-element.md)

#### Concepts

[Default container](default-container.md)

