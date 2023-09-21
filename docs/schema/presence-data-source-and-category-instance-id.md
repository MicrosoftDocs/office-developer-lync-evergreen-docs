---
title: Presence data source and category instance ID
TOCTitle: Presence data source and category instance ID
ms:assetid: 7d68a87c-cd0a-4df4-b8cb-0d33842d5eda
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454680(v=office.15)
ms:contentKeyID: 57093216
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Presence data source and category instance ID


**Applies to:** Lync 2013 | Lync Server 2013

Similar enhanced presence data can be published from various data sources. For example, a presence state can describe the status of a user, a device used by the user, or a meeting scheduled for the user. In Microsoft Lync 2013, they are represented by a user state, a machine state, a phone state, and a calendar state, respectively. Each corresponds to [state category instance value elements](state-category-instance-value-elements.md) category instance that is identified by a unique instance ID.

Contact information is assembled from various data sources including Active Directory Domain Services, Address Book Server, and the user. In Lync 2013 the contact information is published and subscribed to in pieces that are contained in different [contactCard category instance value element](contactcard-category-instance-value-element.md) category instances that are identified by their instance IDs.

In Lync 2013, instance IDs are also used to identify different types of publications of the same presence data. For example, a static user state category instance has an instance ID that is different from that of a time-bound user state category instance.

The following table lists the instance IDs of the category instances that are used by Lync 2013 and that can be subscribed to remotely.


> [!NOTE]
> <P>The LSxx[MD5(key)] notation in the expression of an instance ID means the xx least significant bits of the MD5 hash of a given key.</P>



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
<th><p>Category data</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>User identity as specified in the underlying Active Directory domain, including the display name and email address. This is a read-only category instance.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x1</p></td>
<td><p>User-specified contact information through the <strong>Lync Options</strong> dialog box. Includes the user-specified phone numbers.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x2</p></td>
<td><p>User properties that include the user’s work or home address.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x3</p></td>
<td><p>Contact data obtained from the Address Book Services, including a user's title, company name, office location, and available telephone numbers.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x4</p></td>
<td><p>Server-provisioned user-specific application data, such as the unified communications-enabled voice mail URL.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x5</p></td>
<td><p>Presentity information.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x6</p></td>
<td><p>The title and office location of the user.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-category-instance-value-elements.md">state category instance value elements</a></p></td>
<td><p>0</p></td>
<td><p>Static aggregate state.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x1</p></td>
<td><p>User-bounded aggregate state.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x100000000</p></td>
<td><p>User-bounded aggregate machine state.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x20000000</p></td>
<td><p>Static user state.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x24000000</p></td>
<td><p>Time-bounded user state.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x30000000|LS28[MD5(GRUU)]</p></td>
<td><p>Machine state. The 4 most significant bits of this instance ID value hold a value of 3, and the 28 least significant bits contain the 28 least significant bits of the MD5 hash of the device GRUU value.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x40000000|LS28[MD5(SMTP address)]</p></td>
<td><p>Calendar state for a meeting. The 4 most significant bits of this instance ID value hold a value of 4, and the 28 least significant bits contain the 28 least significant bits of the MD5 hash of the user’s SMTP address.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x50000000|LS28[MD5(SMTP address)]</p></td>
<td><p>Calendar state that contains an activity for an OOF meeting. The 4 most significant bits of the instance ID value hold a value of 4, and the 28 least significant bits contain the 28 least significant bits of the MD5 hash of the user’s SMTP address.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x60000000|LS28[MD5(SMTP address)]</p></td>
<td><p>Calendar state containing an activity for an OOF message. The 4 most significant bits of the instance ID value hold the value of 4, and the 28 least significant bits contain the 28 least significant bits of the MD5 hash of the user’s SMTP address.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x70000000|LS28[MD5(TEL URI)]</p></td>
<td><p>Phone state for a RCC call. The 4 most significant bits of the instance ID value hold the value of 7, and the 28 least significant bits of the instance ID value correspond to the 28 least significant bits of the MD5 hash of the TEL URI of the RCC phone set.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x80000000|LS28[MD5(SIP URI,GRUU)]</p></td>
<td><p>Phone state for a VoIP call. The 4 most significant bits of the instance ID value hold the value of 8, and the 28 least significant bits correspond to the 28 least significant bits of the MD5 hash of a comma-separated string that consists of the user’s SIP URI and the GRRU of the device in use. For example, 0x898E1BEB.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x90000000|LS28[MD5(PSTN URI,GRUU)]</p></td>
<td><p>Phone state for a PSTN phone call. The 4 most significant bits of the instance ID hold the value of 9, and the 28 least significant bits of the instance ID value correspond to the 28 least significant bits of the MD5 hash of a comma-separated string consisting of the PSTN URI and the GRUU of the PSTN phone set.</p></td>
</tr>
<tr class="even">
<td><p>calendarData</p></td>
<td><p>0</p></td>
<td><p>Calendar data for working hours.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x40000000|LS30[MD5(Mailbox URI)]</p></td>
<td><p>A calendar period as a contiguous block of free-busy time slots. The two most significant bits of the instance ID value hold the value 4, and the 30 least significant bits correspond to the 30 least significant bits of the MD5 hash of the URI of the mailbox from which the calendar data is obtained.</p></td>
</tr>
<tr class="even">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Personal note that can be set by the user.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0x40000000|0x00000000|LS28(MD5(Mailbox URI)]</p></td>
<td><p>Static OOF message as provisioned from the Microsoft Exchange store. The 4 most significant bits of the instance ID hold the value 4, and the 28 least significant bits are assigned the 28 least significant bits of the MD5 hash of the URI of the mailbox from which the OOF message is obtained.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x40000000|0x40000000|LS28(MD5(Mailbox URI)]</p></td>
<td><p>Time-bounded OOF message as provisioned from the Exchange store. The 4 most significant bits of the instance ID hold the value 4, and the 28 least significant bits are assigned the 28 least significant bits of the MD5 hash of the URI of the mailbox from which the OOF message is obtained.</p></td>
</tr>
<tr class="odd">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Presence capabilities of the supported modalities.</p></td>
</tr>
<tr class="even">
<td><p><a href="device-category-instance-value-element.md">device category instance value element</a></p></td>
<td><p>LS32[MD5(GRUU)]</p></td>
<td><p>Device information. The instance ID value is the 32 lowest significant bits of the MD5 hash of the device GRUU.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Presence category instances published or used by Lync](presence-category-instances-published-or-used-by-lync.md)

