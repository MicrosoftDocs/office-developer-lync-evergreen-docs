---
title: Self container
TOCTitle: Self container
ms:assetid: 16e2e653-ac09-4746-aabf-56e2d6802486
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454667(v=office.15)
ms:contentKeyID: 57093130
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Self container


_**Applies to:** Lync 2013 | Lync Server 2013_

Self Container has an instance ID value of 1 (one). It is invisible to all users except the container owner or the local user. It is used to cache the user or application data. The data can be used to construct the local user’s contact information, to facilitate presence publication, and to establish communications sessions.

The following category instances are published to this container.

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
<td><p><a href="alerts-category-instance-value-element.md">alerts category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>This category instance contains the <strong>Alerts</strong> pane that the local user can set by using the <strong>Lync Options</strong> panel in Lync 2013. Such options specify how the local user is notified when the user is added to the contact list of some other users or when the local user is in a Do Not Disturb state.</p>
<p>The following example shows an <a href="alerts-category-instance-value-element.md">alerts category instance value element</a> category instance value when a user clears the <strong>Notify me when someone adds me to his or her contact list</strong> option under the <strong>Alerts</strong> pane in the <strong>Lync Options</strong> panel.</p>
<pre class="sourceCode xml" id="cb1"><code class="sourceCode xml"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">&lt;alerts</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/options/alerts&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb1-2" data-line-number="2">   <span class="kw">&lt;notifyAdditionToContactList&gt;</span>false<span class="kw">&lt;/notifyAdditionToContactList&gt;</span></a>
<a class="sourceLine" id="cb1-3" data-line-number="3"><span class="kw">&lt;/alerts&gt;</span></a></code></pre></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>This static bound instance contains one or more time periods designated as the working hours of the local user. The information is provisioned from the Microsoft Exchange Server as the workingHours information.</p>
<p>The following code example is from a <a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a> category instance containing the workingHours information.</p>
<pre class="sourceCode xml" id="cb2"><code class="sourceCode xml"><a class="sourceLine" id="cb2-1" data-line-number="1"><span class="kw">&lt;calendarData</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/calendarData&quot;</span> </a>
<a class="sourceLine" id="cb2-2" data-line-number="2"><span class="ot">              mailboxID=</span><span class="st">&quot;johnd@exchange.contoso.com&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-3" data-line-number="3">   <span class="kw">&lt;WorkingHours</span> </a>
<a class="sourceLine" id="cb2-4" data-line-number="4"><span class="ot">      xmlns:auto-ns1=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/calendarData&quot;</span>                         </a>
<a class="sourceLine" id="cb2-5" data-line-number="5"><span class="ot">      xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/exchange/services/2006/types&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb2-6" data-line-number="6">      <span class="kw">&lt;TimeZone&gt;</span></a>
<a class="sourceLine" id="cb2-7" data-line-number="7">         <span class="kw">&lt;Bias&gt;</span>480<span class="kw">&lt;/Bias&gt;</span></a>
<a class="sourceLine" id="cb2-8" data-line-number="8">         <span class="kw">&lt;StandardTime&gt;</span></a>
<a class="sourceLine" id="cb2-9" data-line-number="9">           <span class="kw">&lt;Bias&gt;</span>0<span class="kw">&lt;/Bias&gt;</span></a>
<a class="sourceLine" id="cb2-10" data-line-number="10">           <span class="kw">&lt;Time&gt;</span>02:00:00<span class="kw">&lt;/Time&gt;</span></a>
<a class="sourceLine" id="cb2-11" data-line-number="11">           <span class="kw">&lt;DayOrder&gt;</span>1<span class="kw">&lt;/DayOrder&gt;</span></a>
<a class="sourceLine" id="cb2-12" data-line-number="12">           <span class="kw">&lt;Month&gt;</span>11<span class="kw">&lt;/Month&gt;</span></a>
<a class="sourceLine" id="cb2-13" data-line-number="13">           <span class="kw">&lt;DayOfWeek&gt;</span>Sunday<span class="kw">&lt;/DayOfWeek&gt;</span></a>
<a class="sourceLine" id="cb2-14" data-line-number="14">         <span class="kw">&lt;/StandardTime&gt;</span></a>
<a class="sourceLine" id="cb2-15" data-line-number="15">         <span class="kw">&lt;DaylightTime&gt;</span></a>
<a class="sourceLine" id="cb2-16" data-line-number="16">           <span class="kw">&lt;Bias&gt;</span>-60<span class="kw">&lt;/Bias&gt;</span></a>
<a class="sourceLine" id="cb2-17" data-line-number="17">           <span class="kw">&lt;Time&gt;</span>02:00:00<span class="kw">&lt;/Time&gt;</span></a>
<a class="sourceLine" id="cb2-18" data-line-number="18">           <span class="kw">&lt;DayOrder&gt;</span>2<span class="kw">&lt;/DayOrder&gt;</span></a>
<a class="sourceLine" id="cb2-19" data-line-number="19">           <span class="kw">&lt;Month&gt;</span>3<span class="kw">&lt;/Month&gt;</span></a>
<a class="sourceLine" id="cb2-20" data-line-number="20">           <span class="kw">&lt;DayOfWeek&gt;</span>Sunday<span class="kw">&lt;/DayOfWeek&gt;</span></a>
<a class="sourceLine" id="cb2-21" data-line-number="21">         <span class="kw">&lt;/DaylightTime&gt;</span></a>
<a class="sourceLine" id="cb2-22" data-line-number="22">     <span class="kw">&lt;/TimeZone&gt;</span></a>
<a class="sourceLine" id="cb2-23" data-line-number="23">     <span class="kw">&lt;WorkingPeriodArray&gt;</span></a>
<a class="sourceLine" id="cb2-24" data-line-number="24">       <span class="kw">&lt;WorkingPeriod&gt;</span></a>
<a class="sourceLine" id="cb2-25" data-line-number="25">         <span class="kw">&lt;DayOfWeek&gt;</span>Monday Tuesday Wednesday Thursday Friday<span class="kw">&lt;/DayOfWeek&gt;</span></a>
<a class="sourceLine" id="cb2-26" data-line-number="26">         <span class="kw">&lt;StartTimeInMinutes&gt;</span>480<span class="kw">&lt;/StartTimeInMinutes&gt;</span></a>
<a class="sourceLine" id="cb2-27" data-line-number="27">         <span class="kw">&lt;EndTimeInMinutes&gt;</span>1020<span class="kw">&lt;/EndTimeInMinutes&gt;</span></a>
<a class="sourceLine" id="cb2-28" data-line-number="28">       <span class="kw">&lt;/WorkingPeriod&gt;</span></a>
<a class="sourceLine" id="cb2-29" data-line-number="29">     <span class="kw">&lt;/WorkingPeriodArray&gt;</span></a>
<a class="sourceLine" id="cb2-30" data-line-number="30">   <span class="kw">&lt;/WorkingHours&gt;</span></a>
<a class="sourceLine" id="cb2-31" data-line-number="31"><span class="kw">&lt;/calendarData&gt;</span></a></code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>A hash dependent on the local user’s mailbox URI.</p></td>
<td><p>This time-bound instance is meant to contain a calendar period of the local user. This calendar period is represented by a contiguous block of free-busy timeslots and is provisioned from the Microsoft Exchange Server as the freeBusy information. For the Self Container, this instance carries an empty value.</p></td>
</tr>
<tr class="even">
<td><p><a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a></p></td>
<td><p></p></td>
<td><p>These category instances contains the <strong>Personal Information Manager</strong> setting, the privacy mode selection, voice mail last access records, and other optional settings that can be configured through the <strong>Lync Options</strong> panel.</p>
<p>The following example shows an <a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a> category instance with privacy mode settings.</p>
<pre class="sourceCode xml" id="cb3"><code class="sourceCode xml"><a class="sourceLine" id="cb3-1" data-line-number="1"><span class="kw">&lt;otherOptions</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/options/otherOptions&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb3-2" data-line-number="2">   <span class="kw">&lt;privacyModeUserSelection&gt;</span>standard<span class="kw">&lt;/privacyModeUserSelection&gt;</span></a>
<a class="sourceLine" id="cb3-3" data-line-number="3">   <span class="kw">&lt;currentPrivacyMode&gt;</span>standard<span class="kw">&lt;/currentPrivacyMode&gt;</span></a>
<a class="sourceLine" id="cb3-4" data-line-number="4">   <span class="kw">&lt;lastQueryPrivacyEnabled&gt;</span>false<span class="kw">&lt;/lastQueryPrivacyEnabled&gt;</span></a>
<a class="sourceLine" id="cb3-5" data-line-number="5">   <span class="kw">&lt;publishActivityHistory&gt;</span>true<span class="kw">&lt;/publishActivityHistory&gt;</span></a>
<a class="sourceLine" id="cb3-6" data-line-number="6">   <span class="kw">&lt;EnableContactSyncUserOption&gt;</span>2<span class="kw">&lt;/EnableContactSyncUserOption&gt;</span></a>
<a class="sourceLine" id="cb3-7" data-line-number="7"><span class="kw">&lt;/otherOptions&gt;</span></a></code></pre>
<p>The following example shows an <a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a> category instance with the <strong>Personal Information Manager</strong> settings.</p>
<pre><code>&lt;otherOptions xmlns=&quot;http://schemas.microsoft.com/2006/09/sip/options/otherOptions&quot;&gt;
  &lt;permissions&gt;
    &lt;personalInformationManager&gt;outlook&lt;/personalInformationManager&gt;
    &lt;autoRetrieveOofFromOutlook&gt;true&lt;/autoRetrieveOofFromOutlook&gt;
    &lt;publishCalendarPresence&gt;true&lt;/publishCalendarPresence&gt;
    &lt;imAutoArchiving&gt;true&lt;/imAutoArchiving&gt;
    &lt;callLogAutoArchiving&gt;false&lt;/callLogAutoArchiving&gt;
    &lt;publishMeetingSubjectAndLocation&gt;true&lt;/publishMeetingSubjectAndLocation&gt;
  &lt;/permissions&gt;
&lt;/otherOptions&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p><a href="rccoptions-category-instance-value-element.md">rccOptions category instance value element</a></p></td>
<td><p></p></td>
<td><p>When PBX phones are supported in Lync Server 2013, published <a href="rccoptions-category-instance-value-element.md">rccOptions category instance value element</a> category instances specify how this kind of phone is controlled in unified communications.</p></td>
</tr>
<tr class="even">
<td><p><a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>The <a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a> category instance contains the server-provisioned user information like the phone lines controlled by the user, the postal address of the user, the telephony mode the user is in, and whether the user has voice mail enabled for unified communications (UC). Each phone line is described by a telephone mode, a TEL URI, and the TEL URI of the line server to support remote call control (RCC). A phone line can be in one of the three types: UC-enabled or VoIP (UC), PBX-based (RCC), and both (Dual). The supported telephony modes are: Uc, Rcc, Dual, and None. The information is provisioned from Active Directory.</p>
<p>The following example shows a <a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a> category instance.</p>
<pre class="sourceCode xml" id="cb5"><code class="sourceCode xml"><a class="sourceLine" id="cb5-1" data-line-number="1"><span class="kw">&lt;userProperties</span><span class="ot"> xmlns=</span><span class="st">&quot;http://schemas.microsoft.com/2006/09/sip/categories&quot;</span><span class="kw">&gt;</span></a>
<a class="sourceLine" id="cb5-2" data-line-number="2">    <span class="kw">&lt;lines&gt;</span></a>
<a class="sourceLine" id="cb5-3" data-line-number="3">        <span class="kw">&lt;line</span><span class="ot"> lineType=</span><span class="st">&quot;Uc&quot;</span><span class="kw">&gt;</span>tel:+14255550180;ext=46666<span class="kw">&lt;/line&gt;</span></a>
<a class="sourceLine" id="cb5-4" data-line-number="4">    <span class="kw">&lt;/lines&gt;</span></a>
<a class="sourceLine" id="cb5-5" data-line-number="5">    <span class="kw">&lt;telephonyMode&gt;</span>Uc<span class="kw">&lt;/telephonyMode&gt;</span></a>
<a class="sourceLine" id="cb5-6" data-line-number="6">    <span class="kw">&lt;exumEnabled&gt;</span>1<span class="kw">&lt;/exumEnabled&gt;</span></a>
<a class="sourceLine" id="cb5-7" data-line-number="7">    <span class="kw">&lt;exumURL&gt;</span>EUM:johnd@contoso.com;phone-context=EX-OCS-SIPSec.exchange.corp.contoso.com<span class="kw">&lt;/exumURL&gt;</span></a>
<a class="sourceLine" id="cb5-8" data-line-number="8"><span class="kw">&lt;/userProperties&gt;</span></a></code></pre>
<p>The <strong>&lt;exumEnabled&gt;</strong> element represents a bit flags indicating whether voice mail is enabled for the user. A bit value of 1 indicates that voice mail is enabled. Otherwise, it is not enabled. The accompanying <strong>&lt;exumURL&gt;</strong> element contains the voice mail URL supported by the Microsoft Exchange Unified Messaging.</p></td>
</tr>
<tr class="odd">
<td><p><a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>The <a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a> category instance contains the sharable user information about the local user. The information includes various phone numbers that remote users can use to contact the local user. It is extracted from the server-provisioned data and/or provided by the user by using the <strong>Lync Options</strong> panel. The <a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a> category instance is published by Lync 2013.</p>
<p>The following example shows a <a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a> category instance.</p>
<pre><code>&lt;userInformation xmlns=&quot;http://schemas.microsoft.com/2006/09/sip/options/userInformation&quot;&gt;
    &lt;callHandlingList&gt;
        &lt;lastPhone&gt;
            &lt;displayString&gt;+114255550150&lt;/displayString&gt;
            &lt;uri&gt;tel:+114255550150&lt;/uri&gt;
        &lt;/lastPhone&gt;
    &lt;/callHandlingList&gt;
    &lt;phones&gt;
        &lt;phone type=&quot;work&quot;&gt;
            &lt;readOnly&gt;true&lt;/readOnly&gt;
            &lt;displayString&gt;+1 (425) 5550160 X63872&lt;/displayString&gt;
            &lt;uri&gt;tel:+14255550160;ext=63872&lt;/uri&gt;
        &lt;/phone&gt;
        &lt;phone type=&quot;mobile&quot;&gt;
            &lt;displayString&gt;+14255550170&lt;/displayString&gt;
            &lt;uri&gt;tel:+14255550170&lt;/uri&gt;
        &lt;/phone&gt;
        &lt;phone type=&quot;home&quot;&gt;
        &lt;/phone&gt;
        &lt;phone type=&quot;other&quot;&gt;
        &lt;/phone&gt;
    &lt;/phones&gt;
&lt;/userInformation&gt;</code></pre></td>
</tr>
</tbody>
</table>


In addition, in-band provisioning data, including server configuration, unified communications policies, enhanced presence publication grammars, or location profile, is also stored in the Self Container. Most unified communications APIs, including the Microsoft Lync 2013 SDK and Microsoft Unified Communications Managed API 4.0 SDK APIs, encapsulate these information with API-specific objects.

## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

