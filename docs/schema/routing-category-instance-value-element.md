---
title: routing category instance value element
TOCTitle: routing category instance value element
ms:assetid: 6dd52f88-c675-4d69-8812-6f275f5d739b
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454776(v=office.15)
ms:contentKeyID: 57093662
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# routing category instance value element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies routing rules to forward incoming calls.

```xml
<ro:routing xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xmlns:xsd="http://www.w3.org/2001/XMLSchema"
       xmlns:ro="http://schemas.microsoft.com/2006/09/sip/routing"
    name="xs:string"
    version="xs:integer">
    <ro:preamble>
       <ro:flags>...</ro:flags>
       <ro:wait>...</ro:wait>
       <ro:list>...</ro:list>
    </ro:preamble>
</ro:routing>
```

ro:routing-type

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
<td><p>Routing rules name. This attribute has a fixed value of &quot;rtcdefault&quot;.</p></td>
</tr>
<tr class="even">
<td><p>version</p></td>
<td><p>Version number of the named routine rules.</p></td>
</tr>
</tbody>
</table>


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
<td><p><a href="routing-preamble-element.md">routing/preamble element</a></p></td>
<td><p>1</p></td>
<td><p>Specific routing rules.</p></td>
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
<td><p>None</p></td>
<td><p>This is a top-level element as the value of an enhanced presence routing category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

Depending on the Options settings enacted for call forwarding, Microsoft Lync 2013 publishes a routing category instance to the following containers:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Container</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>The general settings, including simultaneous ringing, forwarding targets and wait time, for call forwarding are published as a routing category instance of the instance Id value of 0. A breakthrough routing rule targeted to the specified members of Container 400 is published to this container. This ensures that calls made by the specified Friends and Family contacts will not be inadvertently blocked. This routing category instance has an instance Id value of 1.</p></td>
</tr>
<tr class="even">
<td><p>100</p></td>
<td><p>The general settings, including simultaneous ringing, forwarding targets and wait time, for call forwarding are published as a routing category instance of the instance Id value of 0. A breakthrough routing rule targeted to the specified members of Container 400 is published to this container. This ensures that calls made by the user’s Friends and Family contacts will not be inadvertently blocked. This routing category instance has an instance Id value of 1.</p></td>
</tr>
<tr class="odd">
<td><p>200</p></td>
<td><p>The general settings, including simultaneous ringing, forwarding targets and wait time, for call forwarding are published as a routing category instance of the instance Id value of 0. A breakthrough routing rule targeted to the specified members of Container 400 is published to this container. This ensures that calls made by the user’s Friends and family contacts will not be inadvertently blocked. This routing category instance has an instance Id value of 1.</p></td>
</tr>
<tr class="even">
<td><p>300</p></td>
<td><p>The general settings, including simultaneous ringing, forwarding targets and wait time, for call forwarding are published as a routing category instance of the instance Id value of 0. A breakthrough routing rule targeted to the specified members of Container 400 is published to this container. This ensures that calls made by the user’s Friends and family contacts will not be inadvertently blocked. This routing category instance has an instance Id value of 1.</p></td>
</tr>
<tr class="odd">
<td><p>400</p></td>
<td><p>The general settings, including simultaneous ringing, forwarding targets and wait time, for call forwarding are published as a routing category instance of the instance Id value of 0. A breakthrough routing rule targeted to the specified members of Container 400 is published to this container. This ensures that calls made by the user’s Friends and family contacts will not be inadvertently blocked. This routing category instance has an instance Id value of 1.</p></td>
</tr>
<tr class="even">
<td><p>32000</p></td>
<td><p>A routing instance containing the clientflags with block value is published to this container. This is shown as follows.</p>
<pre><code>&lt;routing xmlns=&quot;http://schemas.microsoft.com/02/2006/sip/routing&quot; name=&quot;rtcdefault&quot; version=&quot;1&quot;&gt;
&lt;preamble&gt;
&lt;flags name=&quot;clientflags&quot; value=&quot;block&quot; /&gt;
&lt;/preamble&gt;
&lt;/routing&gt;</code></pre>
<p>This ensures that calls made any members of this container will be blocked.</p></td>
</tr>
</tbody>
</table>


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

#### Concepts

[Default container](default-container.md)

