---
title: Blocked Contacts container
TOCTitle: Blocked Contacts container
ms:assetid: 9ff06195-10d6-4f52-8c2b-f315c93319e3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454669(v=office.15)
ms:contentKeyID: 57093137
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Blocked Contacts container


_**Applies to:** Lync 2013 | Lync Server 2013_

The Blocked Contacts container has a container ID value of 32000. The default access control list contains a single entry for users from the public cloud. This container is used to block its members from accessing the contained presence data and having their calls routed. The blocking is accomplished by publications of the to-be-blocked category instances with empty values and by a publication of the block [routing category instance value element](routing-category-instance-value-element.md) category instance.

The following category instances are published to this container.

Category instances published by Lync Server 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
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

<p>Publication of this contactCard category instance ensures that all user identities are visible, making all the users discoverable by anyone.</p></td>
</tr>
<tr class="even">
<td><p><a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Contains the availability number of the corresponding <a href="state-element_4.md">state[@type='aggregateState'] element</a> category instance in this container. This makes the local user’s presence status available to the container members that use legacy clients. The following is an example of this category instance.</p>

```XML
<legacyInterop availability="18500" xmlns="http://schemas.microsoft.com/2006/09/sip/categories" />
```

<p>The local user’s presence state always appears Offline to the members of this container.</p></td>
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
<th><p>Category name</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="state-element_4.md">state[@type='aggregateState'] element</a></p></td>
<td><p>1</p></td>
<td><p>Contains only the local user’s current availability number. This is shown in the following example.</p>

```XML
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       manual="false" 
       xsi:type="aggregateState">
  <availability>18500</availability>
</state>
```

<p>This publication makes the local user appear offline to the members of this container.</p></td>
</tr>
<tr class="even">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value as shown in the following example.</p>

```XML
<services xmlns="http://schemas.microsoft.com/2006/09/sip/service" />
```

<p>This publication makes the local user’s presence capabilities invisible to members of this container.</p></td>
</tr>
</tbody>
</table>


Category instances published by Lync 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
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

<p>This category instance is meant to contain the local user’s contact information as constructed from the user-configurable options, such as the local user’s home phone number. This publication renders this piece of the local user’s contact information invisible to the members of this container.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>3</p></td>
<td><p>Contains an empty value of this category instance as shown in the following example.</p>

```XML
<contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
</contactCard>
```

<p>This particular contactCard category instance is meant for the local user’s company description and job title, which are obtained from the underlying Microsoft Lync Server 2013 Address Book Server. This publication renders this piece of the local user’s contact information invisible to the members of this container.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>4</p></td>
<td><p>Contains an empty contactCard category instance without the server-provisioned voice mail URL. This is shown in the following example.</p>

```XML
<contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" isUCEnabled="true">
</contactCard>
```

<p>This instance is meant for representing the server-provisioned voice mail URL of the local user when the user has unified communications (UC) enabled. This publication renders the local user’s voice mail URL invisible to the members of this container.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>6</p></td>
<td><p>Contains a contactCard category instance without the intended information about the local user’s display photo and job title. This is shown in the following example.</p>

```XML
<contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
  <delimiter xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/contactcard" 
             xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
  </delimiter>
  <delimiter xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/contactcard" 
             xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
  </delimiter>
</contactCard>
```

<p>This contactCard instance is meant to contain the local user’s job title and display photo. The local user’s display photo is not displayed to the members of this container when this instance is published without this kind of information.</p></td>
</tr>
<tr class="odd">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value as shown as follows.</p>

```XML
<calendarData xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData">
</calendarData>
```

<p>This category instance is meant to contain the local user’s working hours information as obtained from the user’s Microsoft Exchange account. This publication renders this working-hours information invisible to the members of this container.</p></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>A hash dependent on the local user’s email address.</p></td>
<td><p>Contains an empty value for the free-busy information, as shown in the following example.</p>

```XML
<calendarData xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData">
</calendarData>
```

<p>This effectively blocks the container members from accessing the local user’s free-busy information.</p></td>
</tr>
<tr class="odd">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty personal note as shown in the following example.</p>

```XML
<note xmlns="http://schemas.microsoft.com/2006/09/sip/note">
</note>
```

</td>
</tr>
<tr class="even">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>A hash dependent of the local user’s email address.</p></td>
<td><p>Published during an OOF period and when the OOF message is set, this instance contains an empty out-of-facility (OOF) note as shown in the following example.</p>

```XML
<note xmlns="http://schemas.microsoft.com/2006/09/sip/note"></note>
```

<p>This renders the OOF note message invisible to the members of this container.</p></td>
</tr>
<tr class="odd">
<td><p><a href="routing-category-instance-value-element.md">routing category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains a routing instance that contains the block rule. This is shown in the following example.</p>

```XML
<routing xmlns="http://schemas.microsoft.com/02/2006/sip/routing" name="rtcdefault" version="1">
  <preamble>
    <flags name="clientflags" value="block" />
  </preamble>
</routing>
```

<p>This will cause incoming calls from any member of this container blocked and routed to the local user’s voice mail.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

