---
title: routing/preamble/flags element
TOCTitle: routing/preamble/flags element
ms:assetid: c2b91db7-755b-408b-b624-899a77a00ba3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454809(v=office.15)
ms:contentKeyID: 57093938
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# routing/preamble/flags element


**Applies to:** Lync 2013 | Lync Server 2013

Contains the names of specific routing rules for call forwarding.

```xml
<ro:flags xmlns:ro="http://schemas.microsoft.com/2006/09/sip/routing"
    name="string" value="flag-values-list" />
```

ro:flags-type

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
<td><p>name</p></td>
<td><p>Required attribute to specify the name of the specified routing rules. This attribute has a fixed value of &quot;clientflags&quot;.</p></td>
</tr>
<tr class="even">
<td><p>value</p></td>
<td><p>Required attribute to hold a space-separated list of routing rule names. The valid values are listed as follows:</p>
<dl>
<dt>block</dt>
<dd><p>Block calls from the container members.</p>
</dd>
<dt>delegate_ring</dt>
<dd><p>Ring specified delegates.</p>
</dd>
<dt>enablecf</dt>
<dd><p>Enable call forwarding</p>
</dd>
<dt>forward_audio_app_invites</dt>
<dd><p>Forward audio calls</p>
</dd>
<dt>forward_immediate</dt>
<dd><p>Forward any calls immediately</p>
</dd>
<dt>skip_primary</dt>
<dd><p>Do not ring the primary number.</p>
</dd>
<dt>team_ring</dt>
<dd><p>Simultaneous ring all the team members</p>
</dd>
<dt>work_hours</dt>
<dd><p>Forward calls during the specified working-hours period.</p>
</dd>
<dt>&quot;&quot;</dt>
<dd><p>Unspecified</p>
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

