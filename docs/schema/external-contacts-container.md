---
title: External Contacts container
TOCTitle: External Contacts container
ms:assetid: 1fbc9b37-1e50-4358-8a69-45821c918069
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454727(v=office.15)
ms:contentKeyID: 57093428
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# External Contacts container


**Applies to:** Lync 2013 | Lync Server 2013

This container has a container ID value of 100. The default access control list contains a single entry for federated users. Non-private category instances published to this container are visible to all the users of a federated network by default.

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
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-2" data-line-number="2">  <span class="kw">&lt;identity&gt;</span></a>
<a class="sourceLine" id="cb1-3" data-line-number="3">    <span class="kw">&lt;name&gt;</span></a>
<a class="sourceLine" id="cb1-4" data-line-number="4">      <span class="kw">&lt;displayName&gt;</span>John Barr<span class="kw">&lt;/displayName&gt;</span></a>
<a class="sourceLine" id="cb1-5" data-line-number="5">    <span class="kw">&lt;/name&gt;</span></a>
<a class="sourceLine" id="cb1-6" data-line-number="6">    <span class="kw">&lt;email&gt;</span>john.barr@exchange.contoso.com<span class="kw">&lt;/email&gt;</span></a>
<a class="sourceLine" id="cb1-7" data-line-number="7">  <span class="kw">&lt;/identity&gt;</span></a>
<a class="sourceLine" id="cb1-8" data-line-number="8"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Contains the availability number of the local user’s current <a href="state-element_4.md">state[@type='aggregateState'] element</a>. It makes the local user’s presence status available to the container members that use legacy clients. The following is an example of this category instance.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;legacyInterop</span><span class="ot"> availability=</span><span class="st">&quot;3500&quot;</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/categories&quot;</span> <span class="kw">/&gt;</span></a></code></pre></td>
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
<td><p>Contains only the local user’s current availability number. The following is an example of this category instance.</p>
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xsi:type=</span><span class="st">&quot;aggregateState&quot;</span> </a>
<a class="sourceLine" id="cb1-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb1-3" data-line-number="3"><span class="ot">       xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-4" data-line-number="4">  <span class="kw">&lt;availability&gt;</span>3500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb1-5" data-line-number="5"><span class="kw">&lt;/state&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains the endpoint-independent presence capabilities of the local user. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;services</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/service&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-2" data-line-number="2">  <span class="kw">&lt;service</span><span class="ot"> uri=</span><span class="st">&quot;sip:kdeding@microsoft.com&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-3" data-line-number="3">    <span class="kw">&lt;capabilities&gt;</span></a>
<a class="sourceLine" id="cb2-4" data-line-number="4">      <span class="kw">&lt;text</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-5" data-line-number="5">      <span class="kw">&lt;gifInk</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-6" data-line-number="6">      <span class="kw">&lt;isfInk</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;false&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-7" data-line-number="7">      <span class="kw">&lt;applicationSharing</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-8" data-line-number="8">      <span class="kw">&lt;voice</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-9" data-line-number="9">      <span class="kw">&lt;video</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-10" data-line-number="10">      <span class="kw">&lt;contentWhiteboard</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-11" data-line-number="11">      <span class="kw">&lt;contentPoll</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-12" data-line-number="12">      <span class="kw">&lt;contentPowerPoint</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-13" data-line-number="13">      <span class="kw">&lt;contentNativeFile</span><span class="ot"> render=</span><span class="st">&quot;true&quot;</span><span class="ot"> capture=</span><span class="st">&quot;true&quot;</span><span class="ot"> deviceAvailability=</span><span class="st">&quot;3500&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb2-14" data-line-number="14">    <span class="kw">&lt;/capabilities&gt;</span></a>
<a class="sourceLine" id="cb2-15" data-line-number="15">  <span class="kw">&lt;/service&gt;</span></a>
<a class="sourceLine" id="cb2-16" data-line-number="16"><span class="kw">&lt;/services&gt;</span></a></code></pre></td>
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
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-2" data-line-number="2"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre>
<p>This category instance is meant to contain the local user’s contact information as constructed from the user-configurable options, such as the local user’s home phone number. This effectively blocks members of this container from accessing this kind of information.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>3</p></td>
<td><p>Contains the local user’s company description and job title, which are obtained from the underlying Lync Server 2013 Address Book Server. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span></a>
<a class="sourceLine" id="cb2-2" data-line-number="2"><span class="ot">     xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span></a>
<a class="sourceLine" id="cb2-3" data-line-number="3"><span class="ot">     xmlns:xsd=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-4" data-line-number="4">  <span class="kw">&lt;company&gt;</span>Contoso<span class="kw">&lt;/company&gt;</span></a>
<a class="sourceLine" id="cb2-5" data-line-number="5">  <span class="kw">&lt;title&gt;</span>Senior Employee<span class="kw">&lt;/title&gt;</span></a>
<a class="sourceLine" id="cb2-6" data-line-number="6"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>4</p></td>
<td><p>Contains the server-provisioned voice mail URL of the local user when the user has unified communications (UC) enabled. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb3"><code class="sourceCode xml"><a class="sourceLine" id="cb3-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="ot"> isUCEnabled=</span><span class="st">&quot;true&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-2" data-line-number="2">  <span class="kw">&lt;url</span><span class="ot"> type=</span><span class="st">&quot;voicemail&quot;</span><span class="kw">&gt;</span>sip:johnd@contos.com;opaque=app:voicemail;local-resource-path=voicememo<span class="kw">&lt;/url&gt;</span></a>
<a class="sourceLine" id="cb3-3" data-line-number="3"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>6</p></td>
<td><p>Contains the local user’s job title and display photo. This causes the local user’s photo displayed to members of this container. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb4"><code class="sourceCode xml"><a class="sourceLine" id="cb4-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-2" data-line-number="2">  <span class="kw">&lt;title&gt;</span>SENIOR EMPLOYEE<span class="kw">&lt;/title&gt;</span></a>
<a class="sourceLine" id="cb4-3" data-line-number="3">  <span class="kw">&lt;delimiter</span><span class="ot"> xmlns:auto-ns1=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span> </a>
<a class="sourceLine" id="cb4-4" data-line-number="4"><span class="ot">             xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-5" data-line-number="5">  <span class="kw">&lt;/delimiter&gt;</span></a>
<a class="sourceLine" id="cb4-6" data-line-number="6">  <span class="kw">&lt;delimiter</span><span class="ot"> xmlns:auto-ns1=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span> </a>
<a class="sourceLine" id="cb4-7" data-line-number="7"><span class="ot">             xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-8" data-line-number="8">  <span class="kw">&lt;/delimiter&gt;</span></a>
<a class="sourceLine" id="cb4-9" data-line-number="9">  <span class="kw">&lt;displayADPhoto&gt;</span>true<span class="kw">&lt;/displayADPhoto&gt;</span></a>
<a class="sourceLine" id="cb4-10" data-line-number="10">  <span class="kw">&lt;photo</span><span class="ot"> type=</span><span class="st">&quot;enterprise&quot;</span><span class="ot"> updated=</span><span class="st">&quot;2010-05-24T21:08:59Z&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-11" data-line-number="11">    <span class="kw">&lt;uri&gt;&lt;/uri&gt;</span></a>
<a class="sourceLine" id="cb4-12" data-line-number="12">    <span class="kw">&lt;hash&gt;</span>10b394d3bdc9b3f999e44efb5c269dda<span class="kw">&lt;/hash&gt;</span></a>
<a class="sourceLine" id="cb4-13" data-line-number="13">  <span class="kw">&lt;/photo&gt;</span></a>
<a class="sourceLine" id="cb4-14" data-line-number="14"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value. This effectively blocks the external contacts from accessing the local user’s working-hours information that is obtained from the user’s Microsoft Exchange account.</p></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>A hash dependent on the local user’s email address.</p></td>
<td><p>Contains an empty value for the free-busy information, as shown in the following example.</p>
<pre class="sourceCode xml" id="cb5"><code class="sourceCode xml"><a class="sourceLine" id="cb5-1" data-line-number="1"><span class="kw">&lt;calendarData</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/calendarData&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb5-2" data-line-number="2"><span class="kw">&lt;/calendarData&gt;</span></a></code></pre>
<p>This effectively blocks the container members from accessing the local user’s free-busy information.</p></td>
</tr>
<tr class="odd">
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value when the local user is not in the <strong>Do not disturb</strong> availability mode and it contains an availability number of 9500 when the user is in the <strong>Do not disturb</strong> mode. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb6"><code class="sourceCode xml"><a class="sourceLine" id="cb6-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span></a>
<a class="sourceLine" id="cb6-2" data-line-number="2"><span class="ot">        xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span></a>
<a class="sourceLine" id="cb6-3" data-line-number="3"><span class="ot">        xsi:type=</span><span class="st">&quot;userState&quot;</span><span class="ot"> manual=</span><span class="st">&quot;true&quot;</span> <span class="kw">/&gt;</span></a></code></pre>
<p></p></td>
</tr>
<tr class="even">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains a personal note set by the local user. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb7"><code class="sourceCode xml"><a class="sourceLine" id="cb7-1" data-line-number="1"><span class="kw">&lt;note</span><span class="ot"> xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb7-2" data-line-number="2"><span class="ot">      xmlns:xsd=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema&quot;</span> </a>
<a class="sourceLine" id="cb7-3" data-line-number="3"><span class="ot">      xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/note&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb7-4" data-line-number="4">  <span class="kw">&lt;body</span><span class="ot"> type=</span><span class="st">&quot;personal&quot;</span><span class="ot"> uri=</span><span class="st">&quot;&quot;</span><span class="kw">&gt;</span>A message for public<span class="kw">&lt;/body&gt;</span></a>
<a class="sourceLine" id="cb7-5" data-line-number="5"><span class="kw">&lt;/note&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>A hash dependent of the local user’s email address</p></td>
<td><p>Published during an OOF period, this instance contains an out-of-facility (OOF) note with an empty value as shown in the following example.</p>
<pre class="sourceCode xml" id="cb8"><code class="sourceCode xml"><a class="sourceLine" id="cb8-1" data-line-number="1"><span class="kw">&lt;note</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/note&quot;</span><span class="kw">&gt;&lt;/note&gt;</span></a></code></pre>
<p>This effectively prevents the external contacts from viewing the OOF message.</p></td>
</tr>
<tr class="even">
<td><p><a href="routing-category-instance-value-element.md">routing category instance value element</a></p></td>
<td><p></p></td>
<td><p>One or more <a href="routing-category-instance-value-element.md">routing category instance value element</a> category instances that contain the user-configurable routing rules that are used to handle incoming calls from a member of this container. The following is an example of such an instance.</p>
<pre class="sourceCode xml" id="cb9"><code class="sourceCode xml"><a class="sourceLine" id="cb9-1" data-line-number="1"><span class="kw">&lt;routing</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/02/2006/sip/routing&quot;</span> </a>
<a class="sourceLine" id="cb9-2" data-line-number="2"><span class="ot">         name=</span><span class="st">&quot;rtcdefault&quot;</span><span class="ot"> version=</span><span class="st">&quot;2&quot;</span><span class="ot"> minSupportedClientVersion=</span><span class="st">&quot;4.0.0.0&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb9-3" data-line-number="3">  <span class="kw">&lt;preamble&gt;</span></a>
<a class="sourceLine" id="cb9-4" data-line-number="4">    <span class="kw">&lt;flags</span><span class="ot"> name=</span><span class="st">&quot;clientflags&quot;</span><span class="ot"> value=</span><span class="st">&quot;simultaneous_ring&quot;</span><span class="kw">&gt;&lt;/flags&gt;</span></a>
<a class="sourceLine" id="cb9-5" data-line-number="5">    <span class="kw">&lt;wait</span><span class="ot"> name=</span><span class="st">&quot;total&quot;</span><span class="ot"> seconds=</span><span class="st">&quot;20&quot;</span><span class="kw">&gt;&lt;/wait&gt;</span></a>
<a class="sourceLine" id="cb9-6" data-line-number="6">    <span class="kw">&lt;list</span><span class="ot"> name=</span><span class="st">&quot;forwardto&quot;</span><span class="kw">&gt;&lt;/list&gt;</span></a>
<a class="sourceLine" id="cb9-7" data-line-number="7">    <span class="kw">&lt;wait</span><span class="ot"> name=</span><span class="st">&quot;user&quot;</span><span class="ot"> seconds=</span><span class="st">&quot;0&quot;</span><span class="kw">&gt;&lt;/wait&gt;</span></a>
<a class="sourceLine" id="cb9-8" data-line-number="8">    <span class="kw">&lt;wait</span><span class="ot"> name=</span><span class="st">&quot;team1&quot;</span><span class="ot"> seconds=</span><span class="st">&quot;0&quot;</span><span class="kw">&gt;&lt;/wait&gt;</span></a>
<a class="sourceLine" id="cb9-9" data-line-number="9">    <span class="kw">&lt;wait</span><span class="ot"> name=</span><span class="st">&quot;team2&quot;</span><span class="ot"> seconds=</span><span class="st">&quot;0&quot;</span><span class="kw">&gt;&lt;/wait&gt;</span></a>
<a class="sourceLine" id="cb9-10" data-line-number="10">    <span class="kw">&lt;list</span><span class="ot"> name=</span><span class="st">&quot;simultaneous_ring&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb9-11" data-line-number="11">      <span class="kw">&lt;target</span><span class="ot"> uri=</span><span class="st">&quot;sip:+12065551111@contoso.com;user=phone&quot;</span><span class="kw">&gt;&lt;/target&gt;</span></a>
<a class="sourceLine" id="cb9-12" data-line-number="12">    <span class="kw">&lt;/list&gt;</span></a>
<a class="sourceLine" id="cb9-13" data-line-number="13">  <span class="kw">&lt;/preamble&gt;</span></a>
<a class="sourceLine" id="cb9-14" data-line-number="14"><span class="kw">&lt;/routing&gt;</span></a></code></pre></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

