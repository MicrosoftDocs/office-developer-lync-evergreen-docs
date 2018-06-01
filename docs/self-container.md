---
title Self container
TOCTitle Self container
msassetid 16e2e653-ac09-4746-aabf-56e2d6802486
msmtpsurl httpsmsdn.microsoft.comen-uslibraryDn454667(v=office.15)
mscontentKeyID 57093130
ms.date 07242014
mtps_version v=office.15
dev_langs
- xml
---

# Self container


_Applies to Lync 2013  Lync Server 2013_

Self Container has an instance ID value of 1 (one). It is invisible to all users except the container owner or the local user. It is used to cache the user or application data. The data can be used to construct the local user’s contact information, to facilitate presence publication, and to establish communications sessions.

The following category instances are published to this container.

<table>
<colgroup>
<col style="width 33%"/> 
<col style="width 33%"/> 
<col style="width 33%"/>    
</colgroup
<thead>
<tr class="header">
<th><p>Category name</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
<tr>
<thead>
<tbody>
<tr class="odd">
   <td><p>a href=alerts-category-instance-value-element.mdalerts category instance value elementa</p></td>
<td><p>0</p></td>
<td><p>This category instance contains the strongAlertsstrong pane that the local user can set by using the strongLync Optionsstrong panel in Lync 2013. Such options specify how the local user is notified when the user is added to the contact list of some other users or when the local user is in a Do Not Disturb state.</p>
<p>The following example shows an a href=alerts-category-instance-value-element.mdalerts category instance value elementa category instance value when a user clears the strongNotify me when someone adds me to his or her contact liststrong option under the strongAlertsstrong pane in the strongLync Optionsstrong panel.</p>

```XML
alerts xmlns=httpschemas.microsoft.com200609sipoptionsalerts
   notifyAdditionToContactListfalsenotifyAdditionToContactList
alerts
```
<td>
<tr>
<tr class="even">
<td><p>a href="calendardata-category-instance-value-element.mdcalendarData category instance value elementaptd
tdp0ptd
tdpThis static bound instance contains one or more time periods designated as the working hours of the local user. The information is provisioned from the Microsoft Exchange Server as the workingHours information.p
pThe following code example is from a a href=calendardata-category-instance-value-element.mdcalendarData category instance value elementa category instance containing the workingHours information.p

```XML
calendarData xmlns=httpschemas.microsoft.com200609sipcalendarData 
              mailboxID=johnd@exchange.contoso.com
   WorkingHours 
      xmlnsauto-ns1=httpschemas.microsoft.com200609sipcalendarData                         
      xmlns=httpschemas.microsoft.comexchangeservices2006types
      TimeZone
         Bias480Bias
         StandardTime
           Bias0Bias
           Time020000Time
           DayOrder1DayOrder
           Month11Month
           DayOfWeekSundayDayOfWeek
         StandardTime
         DaylightTime
           Bias-60Bias
           Time020000Time
           DayOrder2DayOrder
           Month3Month
           DayOfWeekSundayDayOfWeek
         DaylightTime
     TimeZone
     WorkingPeriodArray
       WorkingPeriod
         DayOfWeekMonday Tuesday Wednesday Thursday FridayDayOfWeek
         StartTimeInMinutes480StartTimeInMinutes
         EndTimeInMinutes1020EndTimeInMinutes
       WorkingPeriod
     WorkingPeriodArray
   WorkingHours
calendarData
```
td
tr
tr class=odd
tdpa href=calendardata-category-instance-value-element.mdcalendarData category instance value elementaptd
tdpA hash dependent on the local user’s mailbox URI.ptd
tdpThis time-bound instance is meant to contain a calendar period of the local user. This calendar period is represented by a contiguous block of free-busy timeslots and is provisioned from the Microsoft Exchange Server as the freeBusy information. For the Self Container, this instance carries an empty value.ptd
tr
tr class=even
tdpa href=otheroptions-category-instance-value-element.mdotherOptions category instance value elementaptd
tdpptd
tdpThese category instances contains the strongPersonal Information Managerstrong setting, the privacy mode selection, voice mail last access records, and other optional settings that can be configured through the strongLync Optionsstrong panel.p
pThe following example shows an a href=otheroptions-category-instance-value-element.mdotherOptions category instance value elementa category instance with privacy mode settings.p

```XML
otherOptions xmlns=httpschemas.microsoft.com200609sipoptionsotherOptions
   privacyModeUserSelectionstandardprivacyModeUserSelection
   currentPrivacyModestandardcurrentPrivacyMode
   lastQueryPrivacyEnabledfalselastQueryPrivacyEnabled
   publishActivityHistorytruepublishActivityHistory
   EnableContactSyncUserOption2EnableContactSyncUserOption
otherOptions
```

pThe following example shows an a href=otheroptions-category-instance-value-element.mdotherOptions category instance value elementa category instance with the strongPersonal Information Managerstrong settings.p
precode&lt;otherOptions xmlns=&quot;httpschemas.microsoft.com200609sipoptionsotherOptions&quot;&gt;
  &lt;permissions&gt;
    &lt;personalInformationManager&gt;outlook&lt;personalInformationManager&gt;
    &lt;autoRetrieveOofFromOutlook&gt;true&lt;autoRetrieveOofFromOutlook&gt;
    &lt;publishCalendarPresence&gt;true&lt;publishCalendarPresence&gt;
    &lt;imAutoArchiving&gt;true&lt;imAutoArchiving&gt;
    &lt;callLogAutoArchiving&gt;false&lt;callLogAutoArchiving&gt;
    &lt;publishMeetingSubjectAndLocation&gt;true&lt;publishMeetingSubjectAndLocation&gt;
  &lt;permissions&gt;
&lt;otherOptions&gt;codepretd
tr
tr class=odd
tdpa href=rccoptions-category-instance-value-element.mdrccOptions category instance value elementaptd
tdpptd
tdpWhen PBX phones are supported in Lync Server 2013, published a href=rccoptions-category-instance-value-element.mdrccOptions category instance value elementa category instances specify how this kind of phone is controlled in unified communications.ptd
tr
tr class=even
tdpa href=userproperties-category-instance-value-element.mduserProperties category instance value elementaptd
tdp0ptd
tdpThe a href=userproperties-category-instance-value-element.mduserProperties category instance value elementa category instance contains the server-provisioned user information like the phone lines controlled by the user, the postal address of the user, the telephony mode the user is in, and whether the user has voice mail enabled for unified communications (UC). Each phone line is described by a telephone mode, a TEL URI, and the TEL URI of the line server to support remote call control (RCC). A phone line can be in one of the three types UC-enabled or VoIP (UC), PBX-based (RCC), and both (Dual). The supported telephony modes are Uc, Rcc, Dual, and None. The information is provisioned from Active Directory.p
pThe following example shows a a href=userproperties-category-instance-value-element.mduserProperties category instance value elementa category instance.p

```XML
userProperties xmlns=httpschemas.microsoft.com200609sipcategories
    lines
        line lineType=Uctel+14255550180;ext=46666line
    lines
    telephonyModeUctelephonyMode
    exumEnabled1exumEnabled
    exumURLEUMjohnd@contoso.com;phone-context=EX-OCS-SIPSec.exchange.corp.contoso.comexumURL
userProperties
```

pThe strong&lt;exumEnabled&gt;strong element represents a bit flags indicating whether voice mail is enabled for the user. A bit value of 1 indicates that voice mail is enabled. Otherwise, it is not enabled. The accompanying strong&lt;exumURL&gt;strong element contains the voice mail URL supported by the Microsoft Exchange Unified Messaging.ptd
tr
tr class=odd
tdpa href=userinformation-category-instance-value-element.mduserInformation category instance value elementaptd
tdp0ptd
tdpThe a href=userinformation-category-instance-value-element.mduserInformation category instance value elementa category instance contains the sharable user information about the local user. The information includes various phone numbers that remote users can use to contact the local user. It is extracted from the server-provisioned data andor provided by the user by using the strongLync Optionsstrong panel. The a href=userinformation-category-instance-value-element.mduserInformation category instance value elementa category instance is published by Lync 2013.p
pThe following example shows a a href=userinformation-category-instance-value-element.mduserInformation category instance value elementa category instance.p
precode&lt;userInformation xmlns=&quot;httpschemas.microsoft.com200609sipoptionsuserInformation&quot;&gt;
    &lt;callHandlingList&gt;
        &lt;lastPhone&gt;
            &lt;displayString&gt;+114255550150&lt;displayString&gt;
            &lt;uri&gt;tel+114255550150&lt;uri&gt;
        &lt;lastPhone&gt;
    &lt;callHandlingList&gt;
    &lt;phones&gt;
        &lt;phone type=&quot;work&quot;&gt;
            &lt;readOnly&gt;true&lt;readOnly&gt;
            &lt;displayString&gt;+1 (425) 5550160 X63872&lt;displayString&gt;
            &lt;uri&gt;tel+14255550160;ext=63872&lt;uri&gt;
        &lt;phone&gt;
        &lt;phone type=&quot;mobile&quot;&gt;
            &lt;displayString&gt;+14255550170&lt;displayString&gt;
            &lt;uri&gt;tel+14255550170&lt;uri&gt;
        &lt;phone&gt;
        &lt;phone type=&quot;home&quot;&gt;
        &lt;phone&gt;
        &lt;phone type=&quot;other&quot;&gt;
        &lt;phone&gt;
    &lt;phones&gt;
&lt;userInformation&gt;codepretd
tr
tbody
table


In addition, in-band provisioning data, including server configuration, unified communications policies, enhanced presence publication grammars, or location profile, is also stored in the Self Container. Most unified communications APIs, including the Microsoft Lync 2013 SDK and Microsoft Unified Communications Managed API 4.0 SDK APIs, encapsulate these information with API-specific objects.

## See also

#### Concepts

[Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md)

