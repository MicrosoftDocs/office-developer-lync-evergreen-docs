---
title: Meeting lobby management
TOCTitle: Meeting lobby management
ms:assetid: 6d642a48-e298-4405-9001-5be2a085ad77
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933072(v=office.15)
ms:contentKeyID: 50877200
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Meeting lobby management

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about meet-now meeting access types in Microsoft Lync 2013 SDK.

**Last modified:** January 07, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Meeting lobby<br />
Lync 2013 meet-now meeting admission types<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Meeting lobby

A Lync 2013 meeting lobby is a logical pre-admission holding area that a meeting presenter uses to preview the identities of people who have a meeting admission key and want to join a meeting. The lobby is used when the admission scope of a meeting includes people who may not have a reason to join a meeting. The presenter has an opportunity to deny access to a person in the lobby when required.

A person waiting in a meeting lobby cannot see the meeting participant list or the other people who are also waiting in the lobby. When admitted from the lobby, a person can see meeting content and participate in the role assigned.

## Lync 2013 meet-now meeting admission types

Meeting admission types define two important aspects of meeting admission. First, they define the scope of admission. That is, they define who can get into the meeting. Second, admission types specify whether a meeting lobby is used to let a presenter confirm meeting admission.

The meeting admission type only applies to users who have a meeting admission key and attempt to dial in to a meeting by entering a conference URL in a browser or dialing an automated attendant telephone number. Persons who are directly added to a meeting by a presenter are invited to join the meeting and bypass any restrictions defined by meeting access.

The following table describes the meeting admission types.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Meeting admission type</p></th>
<th><p>Entry scope</p></th>
<th><p>Lobby active?</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294117(v=office.15)">ConferenceAccessType</a><strong>.Anonymous</strong></p></td>
<td><p>Anyone can enter.</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294117(v=office.15)">Microsoft.Lync.Model.Conversation.ConferenceAccessType</a><strong>.Open</strong></p></td>
<td><p>Anyone in the user’s organization can enter.</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294117(v=office.15)">Microsoft.Lync.Model.Conversation.ConferenceAccessType</a><strong>.Closed</strong></p></td>
<td><p>Anyone in the user’s organization can enter.</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294117(v=office.15)">Microsoft.Lync.Model.Conversation.ConferenceAccessType</a><strong>.Locked</strong></p></td>
<td><p>Only a meeting presenter can enter.</p></td>
<td><p>Yes</p></td>
</tr>
</tbody>
</table>

## See also

  - [Beyond the basics: Lync meetings](beyond-the-basics-lync-meetings.md)

