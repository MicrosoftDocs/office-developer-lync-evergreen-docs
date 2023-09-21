---
title: Control Source property
TOCTitle: Control Source property
ms:assetid: 9e1486d8-450b-4bde-9ade-c83e8a83aa53
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933144(v=office.15)
ms:contentKeyID: 50877280
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Control Source property

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the **Source** property used on all Microsoft Lync 2013 Controls.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Source property overview<br />
Valid types<br />
Expected types of strings<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Source property overview

Use the [Source](https://msdn.microsoft.com/library/hh363511\(v=office.15\)) property to provide contact or group identity. With controls such as PresenceIndicator and ContactCard, the **Source** property identifies the contact to display. With controls such as StartAudioCallButton and StartVideoCallButton, the **Source** property identifies a contact to include in a conversation. The **Source** property is used by the following controls:

  - [PresenceIndicator](https://msdn.microsoft.com/library/hh345947\(v=office.15\)) control

  - [ContactCard](https://msdn.microsoft.com/library/hh379168\(v=office.15\)) control

  - [StartInstantMessagingButton](https://msdn.microsoft.com/library/hh379340\(v=office.15\)) control

  - [StartAudioCallButton](https://msdn.microsoft.com/library/hh378744\(v=office.15\)) control

  - [SendEmailButton](https://msdn.microsoft.com/library/hh379649\(v=office.15\)) control

  - [StartVideoCallButton](https://msdn.microsoft.com/library/hh379584\(v=office.15\)) control

  - [ScheduleMeetingButton](https://msdn.microsoft.com/library/hh363440\(v=office.15\)) control

  - [SendFileButton](https://msdn.microsoft.com/library/hh347610\(v=office.15\)) control

  - [ShareDesktopButton](https://msdn.microsoft.com/library/hh363609\(v=office.15\)) control

## Valid types

The **Source** property has three valid types:

  - [Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\))

  - [DistributionGroup](https://msdn.microsoft.com/library/jj293432\(v=office.15\))

  - [String](http://go.microsoft.com/fwlink/?linkid=131086%26clcid=0x409)

## Expected types of strings

The **Source** property expects the following types of localizable strings:

  - SIP URI

  - SMTP address

  - E.164 phone number

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Tip" alt="Tip" /><strong>Tip</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Observe the following guidelines when using the <strong>Source</strong> property:</p>
<ul>
<li><p>If the value is a string that does not contain the sip: prefix, the control performs a search, using the string specified as a search criteria, and loads the first contact in the result set matching the specified string. This behavior is not deterministic and yields the slowest performance.</p></li>
<li><p>If the value is a SIP URI string qualified by the sip: prefix, the contact is loaded using an exact match of the specified URI. This behavior is deterministic and yields better performance.</p></li>
<li><p>If the value is a <a href="https://msdn.microsoft.com/library/jj266463(v=office.15)">Contact</a> or <a href="https://msdn.microsoft.com/library/jj293432(v=office.15)">DistributionGroup</a> object, it is used without any changes. This behavior is deterministic and yields the best performance.</p></li>
</ul></td>
</tr>
</tbody>
</table>

## See also

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [Lync Controls reference](lync-controls-reference.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

