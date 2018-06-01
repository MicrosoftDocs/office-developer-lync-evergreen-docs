---
title: Aggregation containers
TOCTitle: Aggregation containers
ms:assetid: fa4895ec-df80-45af-b11c-8ec30c145d09
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454670(v=office.15)
ms:contentKeyID: 57093138
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Aggregation containers


_**Applies to:** Lync 2013 | Lync Server 2013_

There are two aggregation containers. The container ID of the first container is 2 and the second container ID is 3. They are not accessible by anyone other than the container owner. The first aggregation container is used by the Microsoft Lync Server 2013 aggregation script to aggregate the endpoint-specific presence states and to generate the endpoint-independent presence capabilities of the presentity. The results are published to the External Contacts (100), Colleagues (200), and Friends and Family (400) containers. The second aggregation container is used to generate the aggregate state category instance for publication in Workgroup Container (300).

## First aggregation container

Microsoft Lync 2013 publishes the following endpoint-specific category instances to the first aggregation container. They are supplied as input to produce aggregated states by the aggregation script whenever this kind of category instance is added, modified, or removed. The first aggregation container is used to produce aggregated presence state ([state\[@type='aggregateState'\] element](state-element_4.md)) for publication in Container 100, 200, and 400.

Category instances published by Lync 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category instance</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="state-element.md">state[@type='userState'] element</a></p></td>
<td><p>0x20000000</p></td>
<td><p>This is a static category instance and represents the presence state of the user. There are two kinds of user states. When the user resets his or her status by using Lync 2013, the event causes this instance to be published. This instance appears in the next example.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
            manual="true" 
            xsi:type="userState">
   <availability>6500</availability>
</state>
```

</td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x24000000</p></td>
<td><p>This is a time-bounded category instance of a user state that contains the Busy or Do Not Disturb availability mode. This instance appears in the next example.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
            manual="true" 
            xsi:type="userState">
   <availability>6500</availability>
</state>
```

</td>
</tr>
<tr class="odd">
<td><p><a href="state-element_2.md">state[@type='machineState'] element</a></p></td>
<td><p>A hash dependent on the device’s GRUU.</p></td>
<td><p>This is a endpoint-bounded category instance and indicates the presence state of a signed-in device. The following shows an example of this instance.</p>
<pre class="sourceCode xml" id="cb3"><code class="sourceCode xml"><a class="sourceLine" id="cb3-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb3-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb3-3" data-line-number="3"><span class="ot">       manual=</span><span class="st">&quot;false&quot;</span><span class="ot"> xsi:type=</span><span class="st">&quot;machineState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-4" data-line-number="4">  <span class="kw">&lt;availability&gt;</span>3500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb3-5" data-line-number="5">  <span class="kw">&lt;endpointLocation&gt;</span>31/East Wing Redmond<span class="kw">&lt;/endpointLocation&gt;</span></a>
<a class="sourceLine" id="cb3-6" data-line-number="6">  <span class="kw">&lt;delimiter</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-7" data-line-number="7">  <span class="kw">&lt;timeZoneBias&gt;</span>420<span class="kw">&lt;/timeZoneBias&gt;</span></a>
<a class="sourceLine" id="cb3-8" data-line-number="8">  <span class="kw">&lt;timeZoneName&gt;</span>Pacific Daylight Time<span class="kw">&lt;/timeZoneName&gt;</span></a>
<a class="sourceLine" id="cb3-9" data-line-number="9">  <span class="kw">&lt;timeZoneAbbreviation&gt;</span>Pacific Daylight Time<span class="kw">&lt;/timeZoneAbbreviation&gt;</span></a>
<a class="sourceLine" id="cb3-10" data-line-number="10">  <span class="kw">&lt;device&gt;</span>computer<span class="kw">&lt;/device&gt;</span></a>
<a class="sourceLine" id="cb3-11" data-line-number="11">  <span class="kw">&lt;end</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-12" data-line-number="12"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="state-element_3.md">state[@type='calendarState'] element</a></p></td>
<td><p>A hash that is dependent on the local user’s SMTP address.</p></td>
<td><p>This is a time-bounded category instance and corresponds to a scheduled meeting or an OOF activity in the user’s calendar. The following shows an example of the calendar state for an OOF activity.</p>
<pre class="sourceCode xml" id="cb4"><code class="sourceCode xml"><a class="sourceLine" id="cb4-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb4-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb4-3" data-line-number="3"><span class="ot">       manual=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb4-4" data-line-number="4"><span class="ot">       uri=</span><span class="st">&quot;johnd@exchange.contoso.com&quot;</span> </a>
<a class="sourceLine" id="cb4-5" data-line-number="5"><span class="ot">       xsi:type=</span><span class="st">&quot;calendarState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-6" data-line-number="6">  <span class="kw">&lt;activity</span><span class="ot"> token=</span><span class="st">&quot;out-of-office&quot;</span><span class="ot"> minAvailability=</span><span class="st">&quot;12000&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb4-7" data-line-number="7"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="state-element_1.md">state[@type='phoneState'] element</a></p></td>
<td><p>A hash dependent on the phone URI and its GRUU.</p></td>
<td><p>This is an endpoint-bounded category instance and is published when a phone conversation is established. The following shows an example of a phone state instance.</p>
<pre class="sourceCode xml" id="cb5"><code class="sourceCode xml"><a class="sourceLine" id="cb5-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb5-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb5-3" data-line-number="3"><span class="ot">       manual=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb5-4" data-line-number="4"><span class="ot">       xsi:type=</span><span class="st">&quot;phoneState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb5-5" data-line-number="5">   <span class="kw">&lt;availability&gt;</span>6500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb5-6" data-line-number="6">   <span class="kw">&lt;activity</span><span class="ot"> token=</span><span class="st">&quot;on-the-phone&quot;</span><span class="ot"> minAvailability=</span><span class="st">&quot;6500&quot;</span><span class="ot"> maxAvailability=</span><span class="st">&quot;8999&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb5-7" data-line-number="7"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="device-category-instance-value-element.md">device category instance value element</a></p></td>
<td><p>MD5 hash of a device GRUU.</p></td>
<td><p>This is an endpoint-bounded category instance and describes a signed-in device, including the device’s capabilities. The following shows an example of a device instance.</p>
<pre class="sourceCode xml" id="cb6"><code class="sourceCode xml"><a class="sourceLine" id="cb6-1" data-line-number="1"><span class="kw">&lt;device</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/device&quot;</span> </a>
<a class="sourceLine" id="cb6-2" data-line-number="2"><span class="ot">        endpointId=</span><span class="st">&quot;458D2A22-9EC7-5D55-B011-F8E31CFE459E&quot;</span> </a>
<a class="sourceLine" id="cb6-3" data-line-number="3"><span class="ot">        gruu=</span><span class="st">&quot;sip:johnd@contoso.com;opaque=user:epid:IiqNRceeVV2wEfjjHP5FngAA;gruu&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb6-4" data-line-number="4">  <span class="kw">&lt;capabilities</span><span class="ot"> preferred=</span><span class="st">&quot;false&quot;</span><span class="ot"> uri=</span><span class="st">&quot;sip:johnd@contoso.com&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb6-5" data-line-number="5">    <span class="kw">&lt;text</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-6" data-line-number="6">    <span class="kw">&lt;gifInk</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-7" data-line-number="7">    <span class="kw">&lt;isfInk</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-8" data-line-number="8">    <span class="kw">&lt;applicationSharing</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-9" data-line-number="9">    <span class="kw">&lt;confInvite</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;true&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-10" data-line-number="10">    <span class="kw">&lt;voice</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-11" data-line-number="11">    <span class="kw">&lt;video</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-12" data-line-number="12">    <span class="kw">&lt;containerIntegrity</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;true&quot;</span><span class="ot"> version=</span><span class="st">&quot;20&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-13" data-line-number="13">    <span class="kw">&lt;breakthrough</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;true&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-14" data-line-number="14">    <span class="kw">&lt;contentWhiteboard</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-15" data-line-number="15">    <span class="kw">&lt;contentPoll</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-16" data-line-number="16">    <span class="kw">&lt;contentPowerPoint</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-17" data-line-number="17">    <span class="kw">&lt;contentNativeFile</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb6-18" data-line-number="18">  <span class="kw">&lt;/capabilities&gt;</span></a>
<a class="sourceLine" id="cb6-19" data-line-number="19">  <span class="kw">&lt;machineName&gt;</span>WindowsCE<span class="kw">&lt;/machineName&gt;</span></a>
<a class="sourceLine" id="cb6-20" data-line-number="20"><span class="kw">&lt;/device&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value when the local user is not in the <strong>Do not disturb</strong> availability mode and contains an availability number of 9500 when the user is in the <strong>Do not disturb</strong> mode. This scenario is shown in the following example.</p>
<pre class="sourceCode xml" id="cb7"><code class="sourceCode xml"><a class="sourceLine" id="cb7-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb7-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb7-3" data-line-number="3"><span class="ot">       xsi:type=</span><span class="st">&quot;userState&quot;</span><span class="ot"> manual=</span><span class="st">&quot;true&quot;</span> <span class="kw">/&gt;</span></a></code></pre>
<p></p></td>
</tr>
</tbody>
</table>


Category instances published by aggregation script

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category instance</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="state-element_5.md">state[@type='aggregateMachineState'] element</a></p></td>
<td><p>0x10000000</p></td>
<td><p>This is a user-bounded category instance and represents the device-independent overall availability and/or activity of a device.</p>
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xsi:type=</span><span class="st">&quot;aggregateMachineState&quot;</span> </a>
<a class="sourceLine" id="cb1-2" data-line-number="2"><span class="ot">       endpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb1-3" data-line-number="3"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span></a>
<a class="sourceLine" id="cb1-4" data-line-number="4"><span class="ot">       xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-5" data-line-number="5">  <span class="kw">&lt;availability&gt;</span>3500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb1-6" data-line-number="6"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="state-element_4.md">state[@type='aggregateState'] element</a></p></td>
<td><p>0x00000001</p></td>
<td><p>This is a user-bounded category instance and represents the endpoint-independent overall availability and/or activity of the user. The following shows an example of this category instance.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xsi:type=</span><span class="st">&quot;aggregateState&quot;</span> </a>
<a class="sourceLine" id="cb2-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb2-3" data-line-number="3"><span class="ot">       xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-4" data-line-number="4">  <span class="kw">&lt;availability&gt;</span>3500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb2-5" data-line-number="5">  <span class="kw">&lt;endpointLocation&gt;</span>31/East Wing Redmond<span class="kw">&lt;/endpointLocation&gt;</span></a>
<a class="sourceLine" id="cb2-6" data-line-number="6">  <span class="kw">&lt;delimiter</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-7" data-line-number="7">  <span class="kw">&lt;timeZoneBias&gt;</span>420<span class="kw">&lt;/timeZoneBias&gt;</span></a>
<a class="sourceLine" id="cb2-8" data-line-number="8">  <span class="kw">&lt;timeZoneName&gt;</span>Pacific Daylight Time<span class="kw">&lt;/timeZoneName&gt;</span></a>
<a class="sourceLine" id="cb2-9" data-line-number="9">  <span class="kw">&lt;timeZoneAbbreviation&gt;</span>Pacific Daylight Time<span class="kw">&lt;/timeZoneAbbreviation&gt;</span></a>
<a class="sourceLine" id="cb2-10" data-line-number="10">  <span class="kw">&lt;device&gt;</span>computer<span class="kw">&lt;/device&gt;</span></a>
<a class="sourceLine" id="cb2-11" data-line-number="11">  <span class="kw">&lt;end</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-12" data-line-number="12"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>This is a user-bounded category instance and it represents the endpoint-independent presence capabilities of the local user.</p>
<pre class="sourceCode xml" id="cb3"><code class="sourceCode xml"><a class="sourceLine" id="cb3-1" data-line-number="1"><span class="kw">&lt;services</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/service&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-2" data-line-number="2">  <span class="kw">&lt;service</span><span class="ot"> uri=</span><span class="st">&quot;sip:johnd@contoso.com&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-3" data-line-number="3">    <span class="kw">&lt;capabilities&gt;</span></a>
<a class="sourceLine" id="cb3-4" data-line-number="4">      <span class="kw">&lt;containerIntegrity</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;true&quot;</span><span class="ot"> version=</span><span class="st">&quot;30&quot;</span> </a>
<a class="sourceLine" id="cb3-5" data-line-number="5"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-6" data-line-number="6"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-7" data-line-number="7">      <span class="kw">&lt;text</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-8" data-line-number="8"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-9" data-line-number="9"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-10" data-line-number="10">      <span class="kw">&lt;gifInk</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-11" data-line-number="11"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-12" data-line-number="12"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-13" data-line-number="13">      <span class="kw">&lt;isfInk</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-14" data-line-number="14"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-15" data-line-number="15"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-16" data-line-number="16">      <span class="kw">&lt;applicationSharing</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-17" data-line-number="17"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-18" data-line-number="18"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-19" data-line-number="19">      <span class="kw">&lt;confInvite</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;true&quot;</span> </a>
<a class="sourceLine" id="cb3-20" data-line-number="20"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;458d2a22-9ec7-5d55-b011-f8e31cfe459e&quot;</span> </a>
<a class="sourceLine" id="cb3-21" data-line-number="21"><span class="ot">              deviceAvailability=</span><span class="st">&quot;15500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-22" data-line-number="22">      <span class="kw">&lt;voice</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-23" data-line-number="23"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-24" data-line-number="24"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-25" data-line-number="25">      <span class="kw">&lt;video</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-26" data-line-number="26"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-27" data-line-number="27"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-28" data-line-number="28">      <span class="kw">&lt;breakthrough</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;true&quot;</span> </a>
<a class="sourceLine" id="cb3-29" data-line-number="29"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;458d2a22-9ec7-5d55-b011-f8e31cfe459e&quot;</span> </a>
<a class="sourceLine" id="cb3-30" data-line-number="30"><span class="ot">              deviceAvailability=</span><span class="st">&quot;15500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-31" data-line-number="31">      <span class="kw">&lt;contentWhiteboard</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-32" data-line-number="32"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-33" data-line-number="33"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-34" data-line-number="34">      <span class="kw">&lt;contentPoll</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-35" data-line-number="35"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-36" data-line-number="36"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-37" data-line-number="37">      <span class="kw">&lt;contentPowerPoint</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-38" data-line-number="38"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-39" data-line-number="39"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-40" data-line-number="40">      <span class="kw">&lt;contentNativeFile</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> publish=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-41" data-line-number="41"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-42" data-line-number="42"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-43" data-line-number="43">      <span class="kw">&lt;ucs</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;true&quot;</span> </a>
<a class="sourceLine" id="cb3-44" data-line-number="44"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-45" data-line-number="45"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-46" data-line-number="46">    <span class="kw">&lt;/capabilities&gt;</span></a>
<a class="sourceLine" id="cb3-47" data-line-number="47">  <span class="kw">&lt;/service&gt;</span></a>
<a class="sourceLine" id="cb3-48" data-line-number="48">  <span class="kw">&lt;service</span><span class="ot"> uri=</span><span class="st">&quot;johnd@exchange.contoso.com&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-49" data-line-number="49">    <span class="kw">&lt;capabilities&gt;</span></a>
<a class="sourceLine" id="cb3-50" data-line-number="50">      <span class="kw">&lt;calendar</span><span class="ot"> render=</span><span class="st">&quot;false&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> publish=</span><span class="st">&quot;true&quot;</span><span class="ot"> version=</span><span class="st">&quot;34210048&quot;</span> </a>
<a class="sourceLine" id="cb3-51" data-line-number="51"><span class="ot">              preferredEndpointId=</span><span class="st">&quot;a47340e3-4723-5558-b5d2-78b850aa2364&quot;</span> </a>
<a class="sourceLine" id="cb3-52" data-line-number="52"><span class="ot">              deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb3-53" data-line-number="53">    <span class="kw">&lt;/capabilities&gt;</span></a>
<a class="sourceLine" id="cb3-54" data-line-number="54">  <span class="kw">&lt;/service&gt;</span></a>
<a class="sourceLine" id="cb3-55" data-line-number="55"><span class="kw">&lt;/services&gt;</span></a></code></pre></td>
</tr>
</tbody>
</table>


## Second aggregation container

Lync 2013 publishes the following endpoint-specific category instances to the second aggregation container. They are supplied as input to produce aggregated states by the aggregation script whenever any such category instance is added, modified, or removed. The second aggregation container is used to produce aggregated presence state ([state\[@type='aggregateState'\] element](state-element_4.md)) for publication in Container 300.

Category instances published by Lync 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category instance</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="state-element.md">state[@type='userState'] element</a></p></td>
<td><p>0x20000000</p></td>
<td><p>This is a static category instance and represents the presence state of the user. When the user resets his or her status by using Lync 2013, the event causes this instance to be published.</p>
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb1-2" data-line-number="2"><span class="ot">            xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb1-3" data-line-number="3"><span class="ot">            manual=</span><span class="st">&quot;true&quot;</span> </a>
<a class="sourceLine" id="cb1-4" data-line-number="4"><span class="ot">            xsi:type=</span><span class="st">&quot;userState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-5" data-line-number="5">  <span class="kw">&lt;availability&gt;</span>3500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb1-6" data-line-number="6"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x24000000</p></td>
<td><p>This is a time-bounded category instance of a user state that contains the Busy availability mode (6500) or the Busy availability mode with urgent-interruptions-only activity token (6900). 6900 is published when the local user sets his or her status to <strong>Do not disturb</strong> on Lync 2013. The following example shows this instance.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb2-2" data-line-number="2"><span class="ot">            xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb2-3" data-line-number="3"><span class="ot">            manual=</span><span class="st">&quot;true&quot;</span> </a>
<a class="sourceLine" id="cb2-4" data-line-number="4"><span class="ot">            xsi:type=</span><span class="st">&quot;userState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-5" data-line-number="5">    <span class="kw">&lt;availability&gt;</span>6900<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb2-6" data-line-number="6">    <span class="kw">&lt;activity</span><span class="ot"> token=</span><span class="st">&quot;urgent-interruptions-only&quot;</span> </a>
<a class="sourceLine" id="cb2-7" data-line-number="7"><span class="ot">              minAvailability=</span><span class="st">&quot;6900&quot;</span> </a>
<a class="sourceLine" id="cb2-8" data-line-number="8"><span class="ot">              maxAvailability=</span><span class="st">&quot;8999&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-9" data-line-number="9"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="state-element_2.md">state[@type='machineState'] element</a></p></td>
<td><p>A hash dependent on the device’s GRUU.</p></td>
<td><p>This is an endpoint-bounded category instance and it indicates the availability of a signed-in device. The following example shows this category instance.</p>
<pre class="sourceCode xml" id="cb3"><code class="sourceCode xml"><a class="sourceLine" id="cb3-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb3-2" data-line-number="2"><span class="ot">            xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb3-3" data-line-number="3"><span class="ot">            manual=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb3-4" data-line-number="4"><span class="ot">            xsi:type=</span><span class="st">&quot;machineState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-5" data-line-number="5">   <span class="kw">&lt;availability&gt;</span>15500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb3-6" data-line-number="6">   <span class="kw">&lt;endpointLocation&gt;</span>31 Redmond<span class="kw">&lt;/endpointLocation&gt;</span></a>
<a class="sourceLine" id="cb3-7" data-line-number="7">   <span class="kw">&lt;delimiter</span><span class="ot"> xmlns:auto-ns1=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span></a>
<a class="sourceLine" id="cb3-8" data-line-number="8"><span class="ot">              xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-9" data-line-number="9">   <span class="kw">&lt;/delimiter&gt;</span></a>
<a class="sourceLine" id="cb3-10" data-line-number="10">   <span class="kw">&lt;timeZoneBias&gt;</span>420<span class="kw">&lt;/timeZoneBias&gt;</span></a>
<a class="sourceLine" id="cb3-11" data-line-number="11">   <span class="kw">&lt;timeZoneName&gt;</span>Pacific Daylight Time<span class="kw">&lt;/timeZoneName&gt;</span></a>
<a class="sourceLine" id="cb3-12" data-line-number="12">   <span class="kw">&lt;device&gt;</span>deskphone<span class="kw">&lt;/device&gt;</span></a>
<a class="sourceLine" id="cb3-13" data-line-number="13">   <span class="kw">&lt;end</span><span class="ot"> xmlns:auto-ns1=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb3-14" data-line-number="14"><span class="ot">        xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-15" data-line-number="15">   <span class="kw">&lt;/end&gt;</span></a>
<a class="sourceLine" id="cb3-16" data-line-number="16"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="state-element_3.md">state[@type='calendarState'] element</a></p></td>
<td><p>A hash dependent on the local user’s SMTP address.</p></td>
<td><p>This is a time-bounded category instance and corresponds to a scheduled meeting or an OOF activity in the user’s calendar. The following is an example of this category instance for an OOF activity.</p>
<pre class="sourceCode xml" id="cb4"><code class="sourceCode xml"><a class="sourceLine" id="cb4-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span></a>
<a class="sourceLine" id="cb4-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb4-3" data-line-number="3"><span class="ot">       manual=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb4-4" data-line-number="4"><span class="ot">       uri=</span><span class="st">&quot;johnd@exchange.contoso.com&quot;</span> </a>
<a class="sourceLine" id="cb4-5" data-line-number="5"><span class="ot">       xsi:type=</span><span class="st">&quot;calendarState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-6" data-line-number="6">  <span class="kw">&lt;activity</span><span class="ot"> token=</span><span class="st">&quot;out-of-office&quot;</span><span class="ot"> minAvailability=</span><span class="st">&quot;12000&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-7" data-line-number="7"><span class="kw">&lt;/activity&gt;</span></a>
<a class="sourceLine" id="cb4-8" data-line-number="8"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="state-element_1.md">state[@type='phoneState'] element</a></p></td>
<td><p>A hash dependent on the phone URI and device GRUU.</p></td>
<td><p>This is an endpoint-bounded category instance and is published when a phone conversation is established. Depending on the deployed topology of Lync Server 2013, three kinds of phone states are possible:</p>
<ul>
<li><p>RCC</p></li>
<li><p>VoIP</p></li>
<li><p>PSTN</p></li>
</ul>
<p>The following is an example of this category instance when the local user is on the phone.</p>
<pre class="sourceCode xml" id="cb5"><code class="sourceCode xml"><a class="sourceLine" id="cb5-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span><span class="ot"> xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span><span class="ot"> manual=</span><span class="st">&quot;false&quot;</span><span class="ot"> xsi:type=</span><span class="st">&quot;phoneState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb5-2" data-line-number="2"><span class="kw">&lt;availability&gt;</span>6500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb5-3" data-line-number="3"><span class="kw">&lt;activity</span><span class="ot"> token=</span><span class="st">&quot;on-the-phone&quot;</span><span class="ot"> minAvailability=</span><span class="st">&quot;6500&quot;</span><span class="ot"> maxAvailability=</span><span class="st">&quot;8999&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb5-4" data-line-number="4"><span class="kw">&lt;/activity&gt;</span></a>
<a class="sourceLine" id="cb5-5" data-line-number="5"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value whether the local user is in the <strong>Do not disturb</strong> availability mode or not. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb6"><code class="sourceCode xml"><a class="sourceLine" id="cb6-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb6-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb6-3" data-line-number="3"><span class="ot">       xsi:type=</span><span class="st">&quot;userState&quot;</span><span class="ot"> manual=</span><span class="st">&quot;true&quot;</span> <span class="kw">/&gt;</span></a></code></pre>
<p></p></td>
</tr>
</tbody>
</table>


Category instances published by aggregation script

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category instance</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="state-element_4.md">state[@type='aggregateState'] element</a></p></td>
<td><p>1</p></td>
<td><p>This is a user-bounded category instance and it represents the endpoint-independent overall presence state of the user. The following is an example of such a category instance.</p>
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xsi:type=</span><span class="st">&quot;aggregateState&quot;</span> </a>
<a class="sourceLine" id="cb1-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb1-3" data-line-number="3"><span class="ot">       xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-4" data-line-number="4">  <span class="kw">&lt;availability&gt;</span>3500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb1-5" data-line-number="5">  <span class="kw">&lt;endpointLocation&gt;</span>31/East Wing Redmond<span class="kw">&lt;/endpointLocation&gt;</span></a>
<a class="sourceLine" id="cb1-6" data-line-number="6">  <span class="kw">&lt;delimiter</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb1-7" data-line-number="7">  <span class="kw">&lt;timeZoneBias&gt;</span>420<span class="kw">&lt;/timeZoneBias&gt;</span></a>
<a class="sourceLine" id="cb1-8" data-line-number="8">  <span class="kw">&lt;timeZoneName&gt;</span>Pacific Daylight Time<span class="kw">&lt;/timeZoneName&gt;</span></a>
<a class="sourceLine" id="cb1-9" data-line-number="9">  <span class="kw">&lt;timeZoneAbbreviation&gt;</span>Pacific Daylight Time<span class="kw">&lt;/timeZoneAbbreviation&gt;</span></a>
<a class="sourceLine" id="cb1-10" data-line-number="10">  <span class="kw">&lt;device&gt;</span>computer<span class="kw">&lt;/device&gt;</span></a>
<a class="sourceLine" id="cb1-11" data-line-number="11">  <span class="kw">&lt;end</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb1-12" data-line-number="12"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
</tbody>
</table>


Lync 2013 uses the second aggregation container to block inbound calls from the user’s work group when the user is in a Do Not Disturb state differently than for other contacts. When the user sets the Do Not Disturb status, Lync 2013 creates a [state\[@type='userState'\] element](state-element.md) category instance in the first aggregation container to contain an availability number of 9500. It also creates a [state\[@type='userState'\] element](state-element.md) category instance in the second aggregation container to contain an availability number 6900 and an activity token of "urgent-interruptions-only". The availability number of 9500 corresponds to a Do Not Disturb state whereas 6900 corresponds to a busy state. This means that the user’s presence status appears to the user’s Workgroup contacts as "Busy – Urgent interruptions only" and to the user’s other contacts as "Do Not Disturb". Thus, calls from any Workgroup contacts are not blocked while calls from other contacts are blocked.

## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

