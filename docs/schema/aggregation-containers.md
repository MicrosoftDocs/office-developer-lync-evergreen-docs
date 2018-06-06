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
   <availability>3500</availability>
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

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       manual="false" xsi:type="machineState">
  <availability>3500</availability>
  <endpointLocation>31/East Wing Redmond</endpointLocation>
  <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
  <timeZoneBias>420</timeZoneBias>
  <timeZoneName>Pacific Daylight Time</timeZoneName>
  <timeZoneAbbreviation>Pacific Daylight Time</timeZoneAbbreviation>
  <device>computer</device>
  <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</state>
```

</td>
</tr>
<tr class="even">
<td><p><a href="state-element_3.md">state[@type='calendarState'] element</a></p></td>
<td><p>A hash that is dependent on the local user’s SMTP address.</p></td>
<td><p>This is a time-bounded category instance and corresponds to a scheduled meeting or an OOF activity in the user’s calendar. The following shows an example of the calendar state for an OOF activity.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       manual="false" 
       uri="johnd@exchange.contoso.com" 
       xsi:type="calendarState">
  <activity token="out-of-office" minAvailability="12000" />
</state>
```

</td>
</tr>
<tr class="odd">
<td><p><a href="state-element_1.md">state[@type='phoneState'] element</a></p></td>
<td><p>A hash dependent on the phone URI and its GRUU.</p></td>
<td><p>This is an endpoint-bounded category instance and is published when a phone conversation is established. The following shows an example of a phone state instance.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       manual="false" 
       xsi:type="phoneState">
   <availability>6500</availability>
   <activity token="on-the-phone" minAvailability="6500" maxAvailability="8999" />
</state>
```

</td>
</tr>
<tr class="even">
<td><p><a href="device-category-instance-value-element.md">device category instance value element</a></p></td>
<td><p>MD5 hash of a device GRUU.</p></td>
<td><p>This is an endpoint-bounded category instance and describes a signed-in device, including the device’s capabilities. The following shows an example of a device instance.</p>

```XML
<device xmlns="http://schemas.microsoft.com/2006/09/sip/device" 
        endpointId="458D2A22-9EC7-5D55-B011-F8E31CFE459E" 
        gruu="sip:johnd@contoso.com;opaque=user:epid:IiqNRceeVV2wEfjjHP5FngAA;gruu">
  <capabilities preferred="false" uri="sip:johnd@contoso.com">
    <text capture="false" render="false" publish="false" />
    <gifInk capture="false" render="false" publish="false" />
    <isfInk capture="false" render="false" publish="false" />
    <applicationSharing capture="false" render="false" publish="false" />
    <confInvite capture="false" render="true" publish="true" />
    <voice capture="true" render="true" publish="false" />
    <video capture="false" render="false" publish="false" />
    <containerIntegrity capture="false" render="false" publish="true" version="20" />
    <breakthrough capture="false" render="false" publish="true" />
    <contentWhiteboard capture="false" render="false" publish="false" />
    <contentPoll capture="false" render="false" publish="false" />
    <contentPowerPoint capture="false" render="false" publish="false" />
    <contentNativeFile capture="false" render="false" publish="false" />
  </capabilities>
  <machineName>WindowsCE</machineName>
</device>
```

</td>
</tr>
<tr class="odd">
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value when the local user is not in the <strong>Do not disturb</strong> availability mode and contains an availability number of 9500 when the user is in the <strong>Do not disturb</strong> mode. This scenario is shown in the following example.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xsi:type="userState" manual="true" />
```
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

```XML
<state xsi:type="aggregateMachineState" 
       endpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns="http://schemas.microsoft.com/2006/09/sip/state">
  <availability>3500</availability>
</state>
```

</td>
</tr>
<tr class="even">
<td><p><a href="state-element_4.md">state[@type='aggregateState'] element</a></p></td>
<td><p>0x00000001</p></td>
<td><p>This is a user-bounded category instance and represents the endpoint-independent overall availability and/or activity of the user. The following shows an example of this category instance.</p>

```XML
<state xsi:type="aggregateState" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xmlns="http://schemas.microsoft.com/2006/09/sip/state">
  <availability>3500</availability>
  <endpointLocation>31/East Wing Redmond</endpointLocation>
  <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
  <timeZoneBias>420</timeZoneBias>
  <timeZoneName>Pacific Daylight Time</timeZoneName>
  <timeZoneAbbreviation>Pacific Daylight Time</timeZoneAbbreviation>
  <device>computer</device>
  <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</state>
```

</td>
</tr>
<tr class="odd">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>This is a user-bounded category instance and it represents the endpoint-independent presence capabilities of the local user.</p>

```XML

<services xmlns="http://schemas.microsoft.com/2006/09/sip/service">
  <service uri="sip:johnd@contoso.com">
    <capabilities>
      <containerIntegrity render="false" capture="false" publish="true" version="30" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <text render="true" capture="true" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <gifInk render="true" capture="false" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <isfInk render="true" capture="false" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <applicationSharing render="true" capture="true" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <confInvite render="true" capture="false" publish="true" 
              preferredEndpointId="458d2a22-9ec7-5d55-b011-f8e31cfe459e" 
              deviceAvailability="15500" />
      <voice render="true" capture="true" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <video render="true" capture="true" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <breakthrough render="false" capture="false" publish="true" 
              preferredEndpointId="458d2a22-9ec7-5d55-b011-f8e31cfe459e" 
              deviceAvailability="15500" />
      <contentWhiteboard render="true" capture="true" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <contentPoll render="true" capture="true" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <contentPowerPoint render="true" capture="true" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <contentNativeFile render="true" capture="true" publish="false" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
      <ucs render="false" capture="false" publish="true" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
    </capabilities>
  </service>
  <service uri="johnd@exchange.contoso.com">
    <capabilities>
      <calendar render="false" capture="false" publish="true" version="34210048" 
              preferredEndpointId="a47340e3-4723-5558-b5d2-78b850aa2364" 
              deviceAvailability="3500" />
    </capabilities>
  </service>
</services>
```

</td>
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

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
            manual="true" 
            xsi:type="userState">
  <availability>3500</availability>
</state>
```
</td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x24000000</p></td>
<td><p>This is a time-bounded category instance of a user state that contains the Busy availability mode (6500) or the Busy availability mode with urgent-interruptions-only activity token (6900). 6900 is published when the local user sets his or her status to <strong>Do not disturb</strong> on Lync 2013. The following example shows this instance.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
            manual="true" 
            xsi:type="userState">
    <availability>6900</availability>
    <activity token="urgent-interruptions-only" 
              minAvailability="6900" 
              maxAvailability="8999" />
</state>
```   

</td>
</tr>
<tr class="odd">
<td><p><a href="state-element_2.md">state[@type='machineState'] element</a></p></td>
<td><p>A hash dependent on the device’s GRUU.</p></td>
<td><p>This is an endpoint-bounded category instance and it indicates the availability of a signed-in device. The following example shows this category instance.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
            manual="false" 
            xsi:type="machineState">
   <availability>15500</availability>
   <endpointLocation>31 Redmond</endpointLocation>
   <delimiter xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/state"
              xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
   </delimiter>
   <timeZoneBias>420</timeZoneBias>
   <timeZoneName>Pacific Daylight Time</timeZoneName>
   <device>deskphone</device>
   <end xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/state" 
        xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
   </end>
</state>
```
</td>
</tr>
<tr class="even">
<td><p><a href="state-element_3.md">state[@type='calendarState'] element</a></p></td>
<td><p>A hash dependent on the local user’s SMTP address.</p></td>
<td><p>This is a time-bounded category instance and corresponds to a scheduled meeting or an OOF activity in the user’s calendar. The following is an example of this category instance for an OOF activity.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       manual="false" 
       uri="johnd@exchange.contoso.com" 
       xsi:type="calendarState">
  <activity token="out-of-office" minAvailability="12000">
</activity>
</state>
```
</td>
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

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" manual="false" xsi:type="phoneState">
<availability>6500</availability>
<activity token="on-the-phone" minAvailability="6500" maxAvailability="8999">
</activity>
</state>
```

</td>
</tr>
<tr class="even">
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value whether the local user is in the <strong>Do not disturb</strong> availability mode or not. This is shown in the following example.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xsi:type="userState" manual="true" />
```

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

```XML
<state xsi:type="aggregateState" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xmlns="http://schemas.microsoft.com/2006/09/sip/state">
  <availability>3500</availability>
  <endpointLocation>31/East Wing Redmond</endpointLocation>
  <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
  <timeZoneBias>420</timeZoneBias>
  <timeZoneName>Pacific Daylight Time</timeZoneName>
  <timeZoneAbbreviation>Pacific Daylight Time</timeZoneAbbreviation>
  <device>computer</device>
  <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</state>
```
</td>
</tr>
</tbody>
</table>


Lync 2013 uses the second aggregation container to block inbound calls from the user’s work group when the user is in a Do Not Disturb state differently than for other contacts. When the user sets the Do Not Disturb status, Lync 2013 creates a [state\[@type='userState'\] element](state-element.md) category instance in the first aggregation container to contain an availability number of 9500. It also creates a [state\[@type='userState'\] element](state-element.md) category instance in the second aggregation container to contain an availability number 6900 and an activity token of "urgent-interruptions-only". The availability number of 9500 corresponds to a Do Not Disturb state whereas 6900 corresponds to a busy state. This means that the user’s presence status appears to the user’s Workgroup contacts as "Busy – Urgent interruptions only" and to the user’s other contacts as "Do Not Disturb". Thus, calls from any Workgroup contacts are not blocked while calls from other contacts are blocked.

## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

