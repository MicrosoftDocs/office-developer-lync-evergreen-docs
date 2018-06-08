---
title: routing/preamble/list/target element
TOCTitle: routing/preamble/list/target element
ms:assetid: 2b506b4a-c83a-4387-a523-75de8a8a4c87
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454781(v=office.15)
ms:contentKeyID: 57093667
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# routing/preamble/list/target element


**Applies to**: Lync Server 2013

Specifies a waiting period before the specified routing rules cease to apply and the incoming calls are sent to the caller’s voicemail.

```xml
<ro:target xmlns:ro="http://schemas.microsoft.com/2006/09/sip/routing"
    uri="string" application="string" />
```

ro:target-type

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
<td><p>uri</p></td>
<td><p>Optional attribute to specify the call-forwarding target as a SIP URI. Either the uri or application attribute must be specified.</p></td>
</tr>
<tr class="even">
<td><p>application</p></td>
<td><p>Optional attribute to specify the call-forwarding target as an application or service. Either the uri or application attribute must be specified.</p></td>
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
<td><p>list</p></td>
<td><p>The target list appearing in the preamble property of the <a href="routing-category-instance-value-element.md">routing category instance value element</a> category instance.</p></td>
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

