---
title: Default container
TOCTitle: Default container
ms:assetid: 23e12cae-3c0a-4268-b4e8-17e1b78f5da8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454665(v=office.15)
ms:contentKeyID: 57093128
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Default container


**Applies to:** Lync 2013 | Lync Server 2013

The Default Container has an ID value of 0 (zero). It is used to allow any remote users who are not a member of any of other containers to access non-private data published to this container or to specify how to route or block incoming calls from such users.

The following category instances are published to the Default Container.

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
<td><p>This category instance contains the display name and email address as the identity of the local user. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;contactCard</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/contactcard&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-2" data-line-number="2">  <span class="kw">&lt;identity&gt;</span></a>
<a class="sourceLine" id="cb1-3" data-line-number="3">    <span class="kw">&lt;name&gt;</span></a>
<a class="sourceLine" id="cb1-4" data-line-number="4">      <span class="kw">&lt;displayName&gt;</span>John Barr<span class="kw">&lt;/displayName&gt;</span></a>
<a class="sourceLine" id="cb1-5" data-line-number="5">    <span class="kw">&lt;/name&gt;</span></a>
<a class="sourceLine" id="cb1-6" data-line-number="6">    <span class="kw">&lt;email&gt;</span>john.barr@exchange.contoso.com<span class="kw">&lt;/email&gt;</span></a>
<a class="sourceLine" id="cb1-7" data-line-number="7">  <span class="kw">&lt;/identity&gt;</span></a>
<a class="sourceLine" id="cb1-8" data-line-number="8"><span class="kw">&lt;/contactCard&gt;</span></a></code></pre>
<p>This contactCard category instance is published by Microsoft Lync Server 2013 and is accessible to the container members whether the local user is signed in or not.</p></td>
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
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Contains an empty value when the local user is not in the <strong>Do not disturb</strong> availability mode and contains an availability number of 9500 when the user is in the <strong>Do not disturb</strong> mode. This is shown in the following example.</p>
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;state</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/state&quot;</span> </a>
<a class="sourceLine" id="cb1-2" data-line-number="2"><span class="ot">       xmlns:xsi=</span><span class="st">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span> </a>
<a class="sourceLine" id="cb1-3" data-line-number="3"><span class="ot">       xsi:type=</span><span class="st">&quot;userState&quot;</span><span class="ot"> manual=</span><span class="st">&quot;true&quot;</span> <span class="kw">/&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="routing-category-instance-value-element.md">routing category instance value element</a></p></td>
<td><p></p></td>
<td><p>One or more <a href="routing-category-instance-value-element.md">routing category instance value element</a> category instances that contain the user-configurable routing rules to handle inbound calls from a member of this container. The following is an example of such an instance.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;routing</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/02/2006/sip/routing&quot;</span> </a>
<a class="sourceLine" id="cb2-2" data-line-number="2"><span class="ot">         name=</span><span class="st">&quot;rtcdefault&quot;</span><span class="ot"> version=</span><span class="st">&quot;2&quot;</span><span class="ot"> minSupportedClientVersion=</span><span class="st">&quot;4.0.0.0&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-3" data-line-number="3">  <span class="kw">&lt;preamble&gt;</span></a>
<a class="sourceLine" id="cb2-4" data-line-number="4">    <span class="kw">&lt;flags</span><span class="ot"> name=</span><span class="st">&quot;clientflags&quot;</span><span class="ot"> value=</span><span class="st">&quot;simultaneous_ring&quot;</span><span class="kw">&gt;&lt;/flags&gt;</span></a>
<a class="sourceLine" id="cb2-5" data-line-number="5">    <span class="kw">&lt;wait</span><span class="ot"> name=</span><span class="st">&quot;total&quot;</span><span class="ot"> seconds=</span><span class="st">&quot;20&quot;</span><span class="kw">&gt;&lt;/wait&gt;</span></a>
<a class="sourceLine" id="cb2-6" data-line-number="6">    <span class="kw">&lt;list</span><span class="ot"> name=</span><span class="st">&quot;forwardto&quot;</span><span class="kw">&gt;&lt;/list&gt;</span></a>
<a class="sourceLine" id="cb2-7" data-line-number="7">    <span class="kw">&lt;wait</span><span class="ot"> name=</span><span class="st">&quot;user&quot;</span><span class="ot"> seconds=</span><span class="st">&quot;0&quot;</span><span class="kw">&gt;&lt;/wait&gt;</span></a>
<a class="sourceLine" id="cb2-8" data-line-number="8">    <span class="kw">&lt;wait</span><span class="ot"> name=</span><span class="st">&quot;team1&quot;</span><span class="ot"> seconds=</span><span class="st">&quot;0&quot;</span><span class="kw">&gt;&lt;/wait&gt;</span></a>
<a class="sourceLine" id="cb2-9" data-line-number="9">    <span class="kw">&lt;wait</span><span class="ot"> name=</span><span class="st">&quot;team2&quot;</span><span class="ot"> seconds=</span><span class="st">&quot;0&quot;</span><span class="kw">&gt;&lt;/wait&gt;</span></a>
<a class="sourceLine" id="cb2-10" data-line-number="10">    <span class="kw">&lt;list</span><span class="ot"> name=</span><span class="st">&quot;simultaneous_ring&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-11" data-line-number="11">      <span class="kw">&lt;target</span><span class="ot"> uri=</span><span class="st">&quot;sip:+12065551111@contoso.com;user=phone&quot;</span><span class="kw">&gt;&lt;/target&gt;</span></a>
<a class="sourceLine" id="cb2-12" data-line-number="12">    <span class="kw">&lt;/list&gt;</span></a>
<a class="sourceLine" id="cb2-13" data-line-number="13">  <span class="kw">&lt;/preamble&gt;</span></a>
<a class="sourceLine" id="cb2-14" data-line-number="14"><span class="kw">&lt;/routing&gt;</span></a></code></pre></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

