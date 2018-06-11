---
title: Workgroup container
TOCTitle: Workgroup container
ms:assetid: 71bfb064-9bda-4785-9dc8-cd0ee8484835
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454668(v=office.15)
ms:contentKeyID: 57093134
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Workgroup container

**Applies to:** Lync 2013 | Lync Server 2013

The Workgroup Container has a container ID value of 300. The default access control list does not contain an entry. When a user changes the privacy relationship with a contact to that of workgroup by using the **Change Privacy Relationship** menu in Microsoft Lync 2013, the affected contact is added as a member of this container.

The following category instances are published to this container.

## Category instances published by Lync Server 2013

<table>
<colgroup>
<col style="width: 40%" />
<col style="width: 10%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category name</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains the local user’s identity that consists of the display name and email address as provisioned from the Active Directory domain. The following is an example of this category instance.</p>

```XML
<contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
  <identity>
    <name>
      <displayName>John Barr</displayName>
    </name>
    <email>john.barr@exchange.contoso.com</email>
  </identity>
</contactCard>
```

</td>
</tr>
<tr class="even">
<td><p><a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Contains the availability number of the local user’s current <a href="state-element_4.md">state[@type='aggregateState'] element</a>. It establishes the local user’s presence status as available to the container members that use legacy clients. The following is an example of this category instance.</p>

```XML
<legacyInterop availability="3500" xmlns="http://schemas.microsoft.com/2006/09/sip/categories" />
```

</td>
</tr>
</tbody>
</table>


## Category instances published by aggregation script

<table>
<colgroup>
<col style="width: 40%" />
<col style="width: 10%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category name</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="state-element_4.md">state[@type='aggregateState'] element</a></p></td>
<td><p>1</p></td>
<td><p>Contains the local user’s current availability number, time zone, and device type. The following is an example of this category instance.</p>

```XML
<state xsi:type="aggregateState" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xmlns="http://schemas.microsoft.com/2006/09/sip/state">
  <availability>3500</availability>
  <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
  <timeZoneBias>420</timeZoneBias>
  <timeZoneName>Pacific Daylight Time</timeZoneName>
  <timeZoneAbbreviation>Pacific Daylight Time</timeZoneAbbreviation>
  <device>computer</device>
  <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</state>
```


<p><b>NOTE</b>: This publication is different from the corresponding one in Container 100 (the External Contacts Container).</p>
</td>
</tr>
<tr class="even">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains the endpoint-independent presence capabilities of the local user. This is shown in the following example.</p>

```XML
<services xmlns="http://schemas.microsoft.com/2006/09/sip/service">
  <service uri="sip:kdeding@microsoft.com">
    <capabilities>
      <text render="true" capture="true" deviceAvailability="3500" />
      <gifInk render="true" capture="false" deviceAvailability="3500" />
      <isfInk render="true" capture="false" deviceAvailability="3500" />
      <applicationSharing render="true" capture="true" deviceAvailability="3500" />
      <voice render="true" capture="true" deviceAvailability="3500" />
      <video render="true" capture="true" deviceAvailability="3500" />
      <contentWhiteboard render="true" capture="true" deviceAvailability="3500" />
      <contentPoll render="true" capture="true" deviceAvailability="3500" />
      <contentPowerPoint render="true" capture="true" deviceAvailability="3500" />
      <contentNativeFile render="true" capture="true" deviceAvailability="3500" />
    </capabilities>
  </service>
</services>
```

</td>
</tr>
</tbody>
</table>


## Category instances published by Lync 2010

<table>
<colgroup>
<col style="width: 40%" />
<col style="width: 10%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category name</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Contains an empty value of this category instance as shown in the following example.</p>

```XML
<contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
</contactCard>
```


<p>This category instance is meant to contain the local user’s contact information as constructed from the user-configurable options, such as the local user’s home phone number.</p> <p>This effectively blocks members of this container from accessing this kind of information.</p>
</td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>3</p></td>
<td><p>Contains the local user’s company description and job title, which are obtained from the underlying Lync Server 2013 Address Book Server.</p> <p>This is shown in the following example.</p>

```XML
<contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard"
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <company>Contoso</company>
  <title>Senior Employee</title>
</contactCard>
```


</td>
</tr>
<tr class="odd">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>4</p></td>
<td><p>Contains the server-provisioned voice mail URL of the local user when the user has unified communications (UC) enabled.</p> <p>This is shown in the following example.</p>

```XML
<contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" isUCEnabled="true">
  <url type="voicemail">sip:johnd@contos.com;opaque=app:voicemail;local-resource-path=voicememo</url>
</contactCard>
```

</td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>6</p></td>
<td><p>Contains the local user’s job title and display photo. This displays the local user’s photo to members of this container.</p> <p>This is shown in the following example.</p>

```XML
<contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
  <title>SENIOR EMPLOYEE</title>
  <delimiter xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/contactcard" 
             xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
  </delimiter>
  <delimiter xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/contactcard" 
             xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
  </delimiter>
  <displayADPhoto>true</displayADPhoto>
  <photo type="enterprise" updated="2010-05-24T21:08:59Z">
    <uri></uri>
    <hash>10b394d3bdc9b3f999e44efb5c269dda</hash>
  </photo>
</contactCard>
```


</td>
</tr>
<tr class="odd">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains the local user’s working-hours information that is obtained from the user’s Microsoft Exchange account.</p>

```XML
<calendarData
      xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData" 
      mailboxID="johnd@exchange.contoso.com">
  <WorkingHours
      xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/calendarData" 
      xmlns="http://schemas.microsoft.com/exchange/services/2006/types">
    <TimeZone>
      <Bias>480</Bias>
      <StandardTime>
        <Bias>0</Bias>
        <Time>02:00:00</Time>
        <DayOrder>1</DayOrder>
        <Month>11</Month>
        <DayOfWeek>Sunday</DayOfWeek>
      </StandardTime>
      <DaylightTime>
        <Bias>-60</Bias>
        <Time>02:00:00</Time>
        <DayOrder>2</DayOrder>
        <Month>3</Month>
        <DayOfWeek>Sunday</DayOfWeek>
      </DaylightTime>
    </TimeZone>
  <WorkingPeriodArray>
    <WorkingPeriod>
      <DayOfWeek>Monday Tuesday Wednesday Thursday Friday</DayOfWeek>
      <StartTimeInMinutes>480</StartTimeInMinutes>
      <EndTimeInMinutes>1020</EndTimeInMinutes>
    </WorkingPeriod>
  </WorkingPeriodArray>
  </WorkingHours>
</calendarData>
```


</td>
</tr>
<tr class="even">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>A hash dependent on the local user’s email address</p></td>
<td><p>Contains the local user’s free-busy information, as shown in the following example.</p>

```XML
<calendarData xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData" 
              mailboxID="johnd@exchange.contoso.com">
  <freeBusy startTime="2010-06-21T07:00:00Z" 
            granularity="PT15M" encodingVersion="1">AAAAAAAAAAAAAAAAVVUAAAAAAAAAAAAAAAAAAAAAAAAAAAAAVQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAVQAAAAAAAAAAAAAAAAAAAAAAAABUUVVVBQAAAAAAAAAA
  </freeBusy>
</calendarData>
```

<p><b>NOTE</b>: The local user’s free-busy information is visible to the Colleagues, Workgroup, and Friends and Family container members, while it is not visible to the External Contacts container members.</p>

</td>
</tr>
<tr class="odd">
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value whether the local user is in the <strong>Do not disturb</strong> availability mode or not.</p> <p>This is shown in the following example.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:type="userState" manual="true" />
```

<p></p></td>
</tr>
<tr class="even">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains a personal note that is set by the local user.</p> <p>This is shown in the following example.</p>

```XML	   
<note xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xmlns:xsd="http://www.w3.org/2001/XMLSchema"
      xmlns="http://schemas.microsoft.com/2006/09/sip/note">
  <body type="personal" uri="">A personal message</body>
</note>
```

</td>
</tr>
<tr class="odd">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>A hash dependent of the local user’s email address</p></td>
<td><p>Published during an OOF period, this instance contains an out-of-facility (OOF) note the local user set in Microsoft Outlook.</p> <p>This is shown in the following example.</p>

```XML
<note xmlns="http://schemas.microsoft.com/2006/09/sip/note">
  <body type="OOF"
        uri="johnd@exchange.contoso.com"
        startTime="2010-06-22T19:00:00Z"
        endTime="2010-06-23T19:00:00Z">A OOF message set in Outlook</body>
</note>
```

<p><b>NOTE</b>: The OOF note is visible to the Colleagues, Workgroup, and Friends and Family container members, while it is not visible to the External Contacts container members.</p>
</td>
</tr>
<tr class="even">
<td><p><a href="notehistory-category-instance-value-element.md">noteHistory category instance value element</a></p></td>
<td><p></p></td>
<td><p>Contains a local user’s previously published personal note, as shown in the following example.</p>

```XML
<noteHistory xmlns="http://schemas.microsoft.com/2006/09/sip/note">
  <body type="personal" uri="">Out to lunch</body>
</noteHistory>
```

<p><b>NOTE</b>: <A href="notehistory-category-instance-value-element.md">noteHistory category instance value element</A> is published to Colleagues, Workgroup, and Friends and Family container members, but not to the External Contacts container.</p> <p>By default, there can be up to three <A href="notehistory-category-instance-value-element.md">noteHistory category instance value element</A> category instances and they correspond to the three most recent <A href="note-category-instance-value-element.md">note category instance value element</A> instances that are published before the current one.</p>
</td>
</tr>
<tr class="odd">
<td><p><a href="routing-category-instance-value-element.md">routing category instance value element</a></p></td>
<td><p>various</p></td>
<td><p>One or more <a href="routing-category-instance-value-element.md">routing category instance value element</a> category instances that contain the user-configurable routing rules to handle incoming calls from a member of this container.</p> <p>The following is an example of such an instance.</p>

```XML
<routing xmlns="http://schemas.microsoft.com/02/2006/sip/routing" 
         name="rtcdefault" version="2" minSupportedClientVersion="4.0.0.0">
  <preamble>
    <flags name="clientflags" value="simultaneous_ring"></flags>
    <wait name="total" seconds="20"></wait>
    <list name="forwardto"></list>
    <wait name="user" seconds="0"></wait>
    <wait name="team1" seconds="0"></wait>
    <wait name="team2" seconds="0"></wait>
    <list name="simultaneous_ring">
      <target uri="sip:+12065551111@contoso.com;user=phone"></target>
    </list>
  </preamble>
</routing>
```

</td>
</tr>
</tbody>
</table>


## See also

- [Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

