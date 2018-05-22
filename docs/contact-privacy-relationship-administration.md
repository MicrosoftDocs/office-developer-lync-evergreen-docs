---
title: Contact privacy relationship administration
TOCTitle: Contact privacy relationship administration
ms:assetid: d2d031e6-7e56-4500-b1dc-1b2fd9fa6f6e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933203(v=office.15)
ms:contentKeyID: 50877345
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Contact privacy relationship administration

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the concept of managing privacy relationships between a signed-in user and other Microsoft Lync 2013 contacts by using the Microsoft Lync 2013 API.

**Last modified:** December 26, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Privacy relationship administration<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Privacy relationship administration

A Lync privacy relationship is a set of five rules that govern how much of a user’s contact card information is visible to other users. The signed-in user does not need to apply one of these privacy relationship rules to the contact list users and other users who subscribe to the signed-in user’s presence. By default, the Colleague privacy relationship rule is applied to the users who belong to the same organization. The default privacy relationship for users outside of the organization is External Contacts.

Figure 1 shows a sample application that lets a user set the privacy relationships of all users in his or her contact list. The contact list is collapsed to the group level in figure 1. When the sample runs, a user expands a group, selects a contact and a privacy relationship rule, and clicks the **Set relationship** button. For information about implementing this feature in your application, see [How to: Administer privacy relationships between Lync users](how-to-administer-privacy-relationships-between-lync-users.md).

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Note" alt="Note" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The set of contact card information that can be published and viewed is known as enhanced presence. Simple presence is the availability of a person for a conversation. To enhance simple presence, Lync 2013 adds personal notes, telephone numbers, calendar information, business title, email address, picture, company, and DND interruption capability.</p></td>
</tr>
</tbody>
</table>

Figure 1. Sample privacy relationship manager UI

  
![Screen shot of privacy relationship manager UI](images/JJ933203.LyncClientSDK_PrivacyRelationshipManagement(Office.15).jpg "Screen shot of privacy relationship manager UI")

### Privacy relationship rules

The following table shows the five rules and lists the restrictions on enhanced presence visibility enforced by each rule.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Rule</p></th>
<th><p>Privacy constraint</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Friends and family</p></td>
<td><p>All contact card information is visible except for meeting details.</p></td>
</tr>
<tr class="even">
<td><p>Workgroup</p></td>
<td><p>All contact card information is visible except for home telephone and other telephone. The contact can interrupt do-not-disturb status.</p></td>
</tr>
<tr class="odd">
<td><p>Colleague</p></td>
<td><p>All contact card information except for meeting details and home, mobile, and other telephone number is visible.</p></td>
</tr>
<tr class="even">
<td><p>External contacts</p></td>
<td><p>The name, title, email address, company, and picture are visible.</p></td>
</tr>
<tr class="odd">
<td><p>Blocked</p></td>
<td><p>The name and email address are shown. The contact cannot reach the user who is using Lync.</p></td>
</tr>
</tbody>
</table>

## Additional resources

  - [How to: Administer privacy relationships between Lync users](how-to-administer-privacy-relationships-between-lync-users.md)

  - [Core concepts: Enhanced presence](core-concepts-enhanced-presence.md)

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

