---
title: ContactInformationType enumeration (Microsoft.Lync.Model)
TOCTitle: ContactInformationType enumeration
ms:assetid: T:Microsoft.Lync.Model.ContactInformationType_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactinformationtype_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598471
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactInformationType.LocationName
- Microsoft.Lync.Model.ContactInformationType.PrimaryEmailAddress
- Microsoft.Lync.Model.ContactInformationType.Office
- Microsoft.Lync.Model.ContactInformationType.CapabilityString
- Microsoft.Lync.Model.ContactInformationType.Description
- Microsoft.Lync.Model.ContactInformationType.Photo
- Microsoft.Lync.Model.ContactInformationType.NextCalendarState
- Microsoft.Lync.Model.ContactInformationType.Reserved2
- Microsoft.Lync.Model.ContactInformationType.Invalid
- Microsoft.Lync.Model.ContactInformationType.DefaultNote
- Microsoft.Lync.Model.ContactInformationType
- Microsoft.Lync.Model.ContactInformationType.Company
- Microsoft.Lync.Model.ContactInformationType.PersonalNote
- Microsoft.Lync.Model.ContactInformationType.IdleStartTime
- Microsoft.Lync.Model.ContactInformationType.MeetingLocation
- Microsoft.Lync.Model.ContactInformationType.IconUrl
- Microsoft.Lync.Model.ContactInformationType.DisplayName
- Microsoft.Lync.Model.ContactInformationType.Availability
- Microsoft.Lync.Model.ContactInformationType.ActivityId
- Microsoft.Lync.Model.ContactInformationType.ContactEndpoints
- Microsoft.Lync.Model.ContactInformationType.NextCalendarStateStartTime
- Microsoft.Lync.Model.ContactInformationType.Activity
- Microsoft.Lync.Model.ContactInformationType.CustomActivity
- Microsoft.Lync.Model.ContactInformationType.OutOfficeNote
- Microsoft.Lync.Model.ContactInformationType.InstantMessageAddresses
- Microsoft.Lync.Model.ContactInformationType.LastName
- Microsoft.Lync.Model.ContactInformationType.FirstName
- Microsoft.Lync.Model.ContactInformationType.Reserved1
- Microsoft.Lync.Model.ContactInformationType.CurrentCalendarState
- Microsoft.Lync.Model.ContactInformationType.IconStream
- Microsoft.Lync.Model.ContactInformationType.ContactType
- Microsoft.Lync.Model.ContactInformationType.Department
- Microsoft.Lync.Model.ContactInformationType.Capabilities
- Microsoft.Lync.Model.ContactInformationType.HomePageUrl
- Microsoft.Lync.Model.ContactInformationType.EmailAddresses
- Microsoft.Lync.Model.ContactInformationType.MeetingSubject
- Microsoft.Lync.Model.ContactInformationType.DefaultNoteType
- Microsoft.Lync.Model.ContactInformationType.Title
- Microsoft.Lync.Model.ContactInformationType.Reserved5
- Microsoft.Lync.Model.ContactInformationType.Reserved7
- Microsoft.Lync.Model.ContactInformationType.TimeZoneBias
- Microsoft.Lync.Model.ContactInformationType.Reserved6
- Microsoft.Lync.Model.ContactInformationType.SourceNetwork
- Microsoft.Lync.Model.ContactInformationType.Reserved3
- Microsoft.Lync.Model.ContactInformationType.TimeZone
- Microsoft.Lync.Model.ContactInformationType.Reserved4
- Microsoft.Lync.Model.ContactInformationType.AttributionString
- Microsoft.Lync.Model.ContactInformationType.CapabilityDetails
- Microsoft.Lync.Model.ContactInformationType.DefaultNotePublishedTime
- Microsoft.Lync.Model.ContactInformationType.IsOutOfOffice
- Microsoft.Lync.Model.ContactInformationType.Reserved10
- Microsoft.Lync.Model.ContactInformationType.Reserved11
- Microsoft.Lync.Model.ContactInformationType.Reserved12
- Microsoft.Lync.Model.ContactInformationType.Reserved8
- Microsoft.Lync.Model.ContactInformationType.Reserved9
- Microsoft.Lync.Model.ContactInformationType.Reserved14
- Microsoft.Lync.Model.ContactInformationType.Reserved13
- Microsoft.Lync.Model.ContactInformationType.Reserved15
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactInformationType enumeration

Enumerates the contact information types.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ContactInformationType
'Usage
Dim instance As ContactInformationType
```

``` csharp
public enum ContactInformationType
```

## Members

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Member name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td>Availability</td>
<td>Contact availability. AvailabilityType enum.</td>
</tr>
<tr class="even">
<td></td>
<td>ActivityId</td>
<td>A token describing current contact availability. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>LocationName</td>
<td>A contact's location. String.</td>
</tr>
<tr class="even">
<td></td>
<td>TimeZone</td>
<td>Time zone. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>TimeZoneBias</td>
<td>The time zone bias is the difference, in minutes, between Coordinated Universal Time (UTC) and the end user’s current local time. All translations between UTC and local time are based on the following formula: UTC = local time + bias.
<p>The time zone bias is the difference, in minutes, between Coordinated Universal Time (UTC) and the end user’s current local time. All translations between UTC and local time are based on the following formula: UTC = local time + bias.</p></td>
</tr>
<tr class="even">
<td></td>
<td>MeetingSubject</td>
<td>Meeting subject. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>MeetingLocation</td>
<td>Meeting location. String.</td>
</tr>
<tr class="even">
<td></td>
<td>Activity</td>
<td>A contact's current Activity(on the phone, in the meeting, available, ...).</td>
</tr>
<tr class="odd">
<td></td>
<td>CustomActivity</td>
<td>A collection of availability descriptions. Array of activity strings.</td>
</tr>
<tr class="even">
<td></td>
<td>IdleStartTime</td>
<td>Time when a contact became idle. DateTime.</td>
</tr>
<tr class="odd">
<td></td>
<td>DisplayName</td>
<td>Display name of a contact. String.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved1</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>PrimaryEmailAddress</td>
<td>The SMTP e-mail address. String.</td>
</tr>
<tr class="even">
<td></td>
<td>EmailAddresses</td>
<td>An unordered collection of contact's addresses. Array of strings.</td>
</tr>
<tr class="odd">
<td></td>
<td>Title</td>
<td>The contact's title. String.</td>
</tr>
<tr class="even">
<td></td>
<td>Company</td>
<td>The contact's company. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>Department</td>
<td>The contact's department. String.</td>
</tr>
<tr class="even">
<td></td>
<td>Office</td>
<td>The contact's office location. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>HomePageUrl</td>
<td>The contact's homepage Url</td>
</tr>
<tr class="even">
<td></td>
<td>Photo</td>
<td>A contact's photo. Stream object.</td>
</tr>
<tr class="odd">
<td></td>
<td>DefaultNote</td>
<td>The default note, shown if no other note is set. String.</td>
</tr>
<tr class="even">
<td></td>
<td>DefaultNoteType</td>
<td>Default note type (i.e. personal or out-of-office). DefaultNoteType enum.</td>
</tr>
<tr class="odd">
<td></td>
<td>PersonalNote</td>
<td>A personal note. String.</td>
</tr>
<tr class="even">
<td></td>
<td>OutOfficeNote</td>
<td>An out-of-office note. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>SourceNetwork</td>
<td>The contact source network. SourceNetworkType enum.</td>
</tr>
<tr class="even">
<td></td>
<td>IconUrl</td>
<td>URL of the icon associated with a contact from a federated public network. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>IconStream</td>
<td>The icon associated with a contact from a federated public network. Stream object.</td>
</tr>
<tr class="even">
<td></td>
<td>ContactEndpoints</td>
<td>Collection of contact's collaboration endpoints (SIP or TEL endpoints). An array of ContactEndpoint objects.</td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved2</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved3</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>NextCalendarStateStartTime</td>
<td>Start time of the next calendar state. DateTime object.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved4</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>CapabilityString</td>
<td>Current contact capability. ('Voice Only', 'IM Only', ...). String.</td>
</tr>
<tr class="even">
<td></td>
<td>Capabilities</td>
<td>Combination of contact capabilities. ContactCapabilities enum.</td>
</tr>
<tr class="odd">
<td></td>
<td>ContactType</td>
<td>Contact's type. ContactType enum.</td>
</tr>
<tr class="even">
<td></td>
<td>Description</td>
<td>Contact's description. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved5</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>FirstName</td>
<td>Contact's first name. String.</td>
</tr>
<tr class="odd">
<td></td>
<td>LastName</td>
<td>Contact's last name. String.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved6</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved7</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved8</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved9</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved10</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>CapabilityDetails</td>
<td>Returns a collection of PresenceCapability objects.</td>
</tr>
<tr class="even">
<td></td>
<td>DefaultNotePublishedTime</td>
<td>The published time for default note</td>
</tr>
<tr class="odd">
<td></td>
<td>CurrentCalendarState</td>
<td>Contact's current calendar state (Free, Busy, Out of office,...). ContactCalendarState enum</td>
</tr>
<tr class="even">
<td></td>
<td>NextCalendarState</td>
<td>Contact's next calendar state (Free, Busy, Out of office,...). ContactCalendarState enum</td>
</tr>
<tr class="odd">
<td></td>
<td>AttributionString</td>
<td>Contact's attribution string</td>
</tr>
<tr class="even">
<td></td>
<td>InstantMessageAddresses</td>
<td>A collection of contact's Instant Messaging addresses. Array of strings.</td>
</tr>
<tr class="odd">
<td></td>
<td>IsOutOfOffice</td>
<td>returns none zero if the contact is out of office.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved11</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved12</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved13</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved14</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved15</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

