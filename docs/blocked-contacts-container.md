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
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-2" data-line-number="2">  <span class="kw">&lt;identity&gt;</span></a>
<a class="sourceLine" id="cb1-3" data-line-number="3">    <span class="kw">&lt;name&gt;</span></a>
<a class="sourceLine" id="cb1-4" data-line-number="4">      <span class="kw">&lt;displayName&gt;</span>John Barr<span class="kw">&lt;/displayName&gt;</span></a>
<a class="sourceLine" id="cb1-5" data-line-number="5">    <span class="kw">&lt;/name&gt;</span></a>
<a class="sourceLine" id="cb1-6" data-line-number="6">    <span class="kw">&lt;email&gt;</span>john.barr@exchange.contoso.com<span class="kw">&lt;/email&gt;</span></a>
<a class="sourceLine" id="cb1-7" data-line-number="7">  <span class="kw">&lt;/identity&gt;</span></a>
<a class="sourceLine" id="cb1-8" data-line-number="8"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre>
<p>Publication of this contactCard category instance ensures that all user identities are visible, making all the users discoverable by anyone.</p></td>
</tr>
<tr class="even">
<td><p><a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Contains the availability number of the corresponding <a href="state-element_4.md">state[@type='aggregateState'] element</a> category instance in this container. This makes the local user’s presence status available to the container members that use legacy clients. The following is an example of this category instance.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;legacyInterop</span><span class="ot"> availability=</span><span class="st">&quot;18500&quot;</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/categories&quot;</span> <span class="kw">/&gt;</span></a></code></pre>
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
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb1-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb1-3" data-line-number="3"><span class="ot">       manual=</span><span class="st">&quot;false&quot;</span> </a>
<a class="sourceLine" id="cb1-4" data-line-number="4"><span class="ot">       xsi:type=</span><span class="st">&quot;aggregateState&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-5" data-line-number="5">  <span class="kw">&lt;availability&gt;</span>18500<span class="kw">&lt;/availability&gt;</span></a>
<a class="sourceLine" id="cb1-6" data-line-number="6"><span class="kw">&lt;/state&gt;</span></a></code></pre>
<p>This publication makes the local user appear offline to the members of this container.</p></td>
</tr>
<tr class="even">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value as shown in the following example.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;services</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/service&quot;</span> <span class="kw">/&gt;</span></a></code></pre>
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
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-2" data-line-number="2"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre>
<p>This category instance is meant to contain the local user’s contact information as constructed from the user-configurable options, such as the local user’s home phone number. This publication renders this piece of the local user’s contact information invisible to the members of this container.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>3</p></td>
<td><p>Contains an empty value of this category instance as shown in the following example.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-2" data-line-number="2"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre>
<p>This particular contactCard category instance is meant for the local user’s company description and job title, which are obtained from the underlying Microsoft Lync Server 2013 Address Book Server. This publication renders this piece of the local user’s contact information invisible to the members of this container.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>4</p></td>
<td><p>Contains an empty contactCard category instance without the server-provisioned voice mail URL. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb3"><code class="sourceCode xml"><a class="sourceLine" id="cb3-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="ot"> isUCEnabled=</span><span class="st">&quot;true&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-2" data-line-number="2"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre>
<p>This instance is meant for representing the server-provisioned voice mail URL of the local user when the user has unified communications (UC) enabled. This publication renders the local user’s voice mail URL invisible to the members of this container.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>6</p></td>
<td><p>Contains a contactCard category instance without the intended information about the local user’s display photo and job title. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb4"><code class="sourceCode xml"><a class="sourceLine" id="cb4-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-2" data-line-number="2">  <span class="kw">&lt;delimiter</span><span class="ot"> xmlns:auto-ns1=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span> </a>
<a class="sourceLine" id="cb4-3" data-line-number="3"><span class="ot">             xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-4" data-line-number="4">  <span class="kw">&lt;/delimiter&gt;</span></a>
<a class="sourceLine" id="cb4-5" data-line-number="5">  <span class="kw">&lt;delimiter</span><span class="ot"> xmlns:auto-ns1=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span> </a>
<a class="sourceLine" id="cb4-6" data-line-number="6"><span class="ot">             xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/commontypes&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb4-7" data-line-number="7">  <span class="kw">&lt;/delimiter&gt;</span></a>
<a class="sourceLine" id="cb4-8" data-line-number="8"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre>
<p>This contactCard instance is meant to contain the local user’s job title and display photo. The local user’s display photo is not displayed to the members of this container when this instance is published without this kind of information.</p></td>
</tr>
<tr class="odd">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value as shown as follows.</p>
<pre class="sourceCode xml" id="cb5"><code class="sourceCode xml"><a class="sourceLine" id="cb5-1" data-line-number="1"><span class="kw">&lt;calendarData</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/calendarData&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb5-2" data-line-number="2"><span class="kw">&lt;/calendarData&gt;</span></a></code></pre>
<p>This category instance is meant to contain the local user’s working hours information as obtained from the user’s Microsoft Exchange account. This publication renders this working-hours information invisible to the members of this container.</p></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>A hash dependent on the local user’s email address.</p></td>
<td><p>Contains an empty value for the free-busy information, as shown in the following example.</p>
<pre class="sourceCode xml" id="cb6"><code class="sourceCode xml"><a class="sourceLine" id="cb6-1" data-line-number="1"><span class="kw">&lt;calendarData</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/calendarData&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb6-2" data-line-number="2"><span class="kw">&lt;/calendarData&gt;</span></a></code></pre>
<p>This effectively blocks the container members from accessing the local user’s free-busy information.</p></td>
</tr>
<tr class="odd">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty personal note as shown in the following example.</p>
<pre class="sourceCode xml" id="cb7"><code class="sourceCode xml"><a class="sourceLine" id="cb7-1" data-line-number="1"><span class="kw">&lt;note</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/note&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb7-2" data-line-number="2"><span class="kw">&lt;/note&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>A hash dependent of the local user’s email address.</p></td>
<td><p>Published during an OOF period and when the OOF message is set, this instance contains an empty out-of-facility (OOF) note as shown in the following example.</p>
<pre class="sourceCode xml" id="cb8"><code class="sourceCode xml"><a class="sourceLine" id="cb8-1" data-line-number="1"><span class="kw">&lt;note</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/note&quot;</span><span class="kw">&gt;&lt;/note&gt;</span></a></code></pre>
<p>This renders the OOF note message invisible to the members of this container.</p></td>
</tr>
<tr class="odd">
<td><p><a href="routing-category-instance-value-element.md">routing category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains a routing instance that contains the block rule. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb9"><code class="sourceCode xml"><a class="sourceLine" id="cb9-1" data-line-number="1"><span class="kw">&lt;routing</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/02/2006/sip/routing&quot;</span><span class="ot"> name=</span><span class="st">&quot;rtcdefault&quot;</span><span class="ot"> version=</span><span class="st">&quot;1&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb9-2" data-line-number="2">  <span class="kw">&lt;preamble&gt;</span></a>
<a class="sourceLine" id="cb9-3" data-line-number="3">    <span class="kw">&lt;flags</span><span class="ot"> name=</span><span class="st">&quot;clientflags&quot;</span><span class="ot"> value=</span><span class="st">&quot;block&quot;</span> <span class="kw">/&gt;</span></a>
<a class="sourceLine" id="cb9-4" data-line-number="4">  <span class="kw">&lt;/preamble&gt;</span></a>
<a class="sourceLine" id="cb9-5" data-line-number="5"><span class="kw">&lt;/routing&gt;</span></a></code></pre>
<p>This will cause incoming calls from any member of this container blocked and routed to the local user’s voice mail.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

