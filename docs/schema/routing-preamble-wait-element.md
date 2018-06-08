---
title: routing/preamble/wait element
TOCTitle: routing/preamble/wait element
ms:assetid: 0332a6ca-7d3d-4cc2-928d-5266da5c5d50
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454782(v=office.15)
ms:contentKeyID: 57093669
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# routing/preamble/wait element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies a waiting period before the specified routing rules cease to apply and the incoming calls are sent to the caller’s voicemail.

```xml
<ro:wait xmlns:ro="http://schemas.microsoft.com/2006/09/sip/routing"
    name="wait-names" seconds="non negative integer" />
```

ro:wait-type

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
<td><p>seconds</p></td>
<td><p>Required attribute to specify the number of seconds for this waiting period.</p></td>
</tr>
<tr class="even">
<td><p>name</p></td>
<td><p>Required attribute to specify the type of waiting period. The valid wait types are listed as follows:</p>
<dl>
<dt>total</dt>
<dd><p>Waiting period for all</p>
</dd>
<dt>user</dt>
<dd><p>Waiting period for the specified users.</p>
</dd>
<dt>team1</dt>
<dd><p>Waiting period for the specified team</p>
</dd>
<dt>team2</dt>
<dd><p>Waiting period for the specified team.</p>
</dd>
</dl></td>
</tr>
</tbody>
</table>


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
<td><p><a href="routing-preamble-element.md">routing/preamble element</a></p></td>
<td><p>The preamble property of the <a href="routing-category-instance-value-element.md">routing category instance value element</a> category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

None

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

