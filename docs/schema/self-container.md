---
title: Self container
TOCTitle: Self container
ms:assetid: 16e2e653-ac09-4746-aabf-56e2d6802486
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454667(v=office.15)
ms:contentKeyID: 57093130
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Self container


**Applies to:** Lync 2013 | Lync Server 2013

Self Container has an instance ID value of 1 (one). It's invisible to all users except the container owner or the local user. It's used to cache the user or application data. The data can be used to construct the local user’s contact information, to facilitate presence publication, and to establish communications sessions.

The following category instances are published to this container.

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
<td><p><a href="alerts-category-instance-value-element.md">alerts category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>This category instance contains the <strong>Alerts</strong> pane that the local user can set by using the <strong>Lync Options</strong> panel in Lync 2013. Such options specify how the local user is notified when the user is added to the contact list of some other users or when the local user is in a Do Not Disturb state.

The following example shows an [alerts category instance value element](alerts-category-instance-value-element.md) category instance value when a user clears the Notify me <strong>when someone adds me to his or her contact list</strong> option under the <strong>Alerts</strong> pane in the <strong>Lync Options</strong> panel.</p>

```XML
<alerts xmlns="http://schemas.microsoft.com/2006/09/sip/options/alerts">
   <notifyAdditionToContactList>false</notifyAdditionToContactList>
</alerts>
```

</td>
</tr>
<tr class="even">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>This static bound instance contains one or more time periods designated as the working hours of the local user. The information is provisioned from the Microsoft Exchange Server as the <strong>workingHours</strong> information.

The following code example is from a [calendarData category instance value element](calendardata-category-instance-value-element.md) category instance containing the workingHours information.</p>

```XML
<calendarData xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData" 
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
<tr class="odd">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>A hash dependent on the local user’s mailbox URI.</p></td>
<td><p>This time-bound instance is meant to contain a calendar period of the local user. This calendar period is represented by a contiguous block of free-busy timeslots and is provisioned from the Microsoft Exchange Server as the <strong>freeBusy</strong> information. For the Self Container, this instance carries an empty value.</p>


</td>
</tr>
<tr class="even">
<td><p><a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a></p></td>
<td><p></p></td>
<td><p>These category instances contains the <strong>Personal Information Manager</strong> setting, the privacy mode selection, voice mail last access records, and other optional settings that can be configured through the <strong>Lync Options</strong> panel.

The following example shows an [otherOptions category instance value element](otheroptions-category-instance-value-element.md) category instance with privacy mode settings.</p>

```XML
<otherOptions xmlns="http://schemas.microsoft.com/2006/09/sip/options/otherOptions">
   <privacyModeUserSelection>standard</privacyModeUserSelection>
   <currentPrivacyMode>standard</currentPrivacyMode>
   <lastQueryPrivacyEnabled>false</lastQueryPrivacyEnabled>
   <publishActivityHistory>true</publishActivityHistory>
   <EnableContactSyncUserOption>2</EnableContactSyncUserOption>
</otherOptions>
```

The following example shows an [otherOptions category instance value element](otheroptions-category-instance-value-element.md) category instance with the Personal Information <strong>Manager</strong> settings.

```
<otherOptions xmlns="http://schemas.microsoft.com/2006/09/sip/options/otherOptions">
  <permissions>
    <personalInformationManager>outlook</personalInformationManager>
    <autoRetrieveOofFromOutlook>true</autoRetrieveOofFromOutlook>
    <publishCalendarPresence>true</publishCalendarPresence>
    <imAutoArchiving>true</imAutoArchiving>
    <callLogAutoArchiving>false</callLogAutoArchiving>
    <publishMeetingSubjectAndLocation>true</publishMeetingSubjectAndLocation>
  </permissions>
</otherOptions>
```

</td>
</tr>
<tr class="odd">
<td><p><a href="rccoptions-category-instance-value-element.md">rccOptions category instance value element</a></p></td>
<td><p></p></td>
<td><p></p>

When PBX phones are supported in Lync Server 2013, published [rccOptions category instance value element](rccoptions-category-instance-value-element.md) category instances specify how this kind of phone is controlled in unified communications.

</td>
</tr>
<tr class="even">
<td><p><a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>The <a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a> category instance contains the server-provisioned user information like the phone lines controlled by the user, the postal address of the user, the telephony mode the user is in, and whether the user has voice mail enabled for unified communications (UC). Each phone line is described by a telephone mode, a TEL URI, and the TEL URI of the line server to support remote call control (RCC). A phone line can be in one of the three types: UC-enabled or VoIP (UC), PBX-based (RCC), and both (Dual). The supported telephony modes are: Uc, Rcc, Dual, and None. The information is provisioned from Active Directory.

The following example shows a [userProperties category instance value element](userproperties-category-instance-value-element.md) category instance.</p>

```XML
<userProperties xmlns="http://schemas.microsoft.com/2006/09/sip/categories">
    <lines>
        <line lineType="Uc">tel:+14255550180;ext=46666</line>
    </lines>
    <telephonyMode>Uc</telephonyMode>
    <exumEnabled>1</exumEnabled>
    <exumURL>EUM:johnd@contoso.com;phone-context=EX-OCS-SIPSec.exchange.corp.contoso.com</exumURL>
</userProperties>
```

The &lt;<strong>exumEnabled</strong>&gt; element represents a bit flags indicating whether voice mail is enabled for the user. A bit value of 1 indicates that voice mail is enabled. Otherwise, it's not enabled. The accompanying &lt;<strong>exumURL</strong>&gt; element contains the voice mail URL supported by the Microsoft Exchange Unified Messaging.

</td>
</tr>
<tr class="odd">
<td><p><a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>The <a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a> category instance contains the sharable user information about the local user. The information includes various phone numbers that remote users can use to contact the local user. It's extracted from the server-provisioned data and/or provided by the user by using the <strong>Lync Options</strong> panel. The <a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a> category instance is published by Lync 2013.

The following example shows a [userInformation category instance value element](userinformation-category-instance-value-element.md) category instance.</p>

```
<userInformation xmlns="http://schemas.microsoft.com/2006/09/sip/options/userInformation">
    <callHandlingList>
        <lastPhone>
            <displayString>+114255550150</displayString>
            <uri>tel:+114255550150</uri>
        </lastPhone>
    </callHandlingList>
    <phones>
        <phone type="work">
            <readOnly>true</readOnly>
            <displayString>+1 (425) 5550160 X63872</displayString>
            <uri>tel:+14255550160;ext=63872</uri>
        </phone>
        <phone type="mobile">
            <displayString>+14255550170</displayString>
            <uri>tel:+14255550170</uri>
        </phone>
        <phone type="home">
        </phone>
        <phone type="other">
        </phone>
    </phones>
</userInformation>

```
</td>
</tr>
</tbody>
</table>

<p>In addition, in-band provisioning data, including server configuration, unified communications policies, enhanced presence publication grammars, or location profile, is also stored in the Self Container. Most unified communications APIs, including the Microsoft Lync 2013 SDK and Microsoft Unified Communications Managed API 4.0 SDK APIs, encapsulate these information with API-specific objects.</p>



## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md) 
