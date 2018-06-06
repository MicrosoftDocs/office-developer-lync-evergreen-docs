---
title: Distribution groups
TOCTitle: Distribution groups
ms:assetid: 1a363768-c89e-41e1-a80a-c88799730ef7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937268(v=office.15)
ms:contentKeyID: 50877086
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Distribution groups

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the Lync 2013 distribution group and the classes and events in the Microsoft Lync 2013 SDK that let you programmatically iterate on the contacts and any nested distribution groups.

**Last modified:** December 10, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Lync 2013 distribution groups<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Lync 2013 distribution groups

A Lync 2013 distribution group is a collection of contacts and can nest other distribution groups. A distribution group is an Active Directory directory service group that can be modified using an Exchange Server 2013 Exchange Administration Center console. You cannot modify a distribution group by using the Lync 2013 client or a Microsoft Lync Server 2013 component such as a cmdlet or Microsoft Lync Server 2013 SDK.

The state of a distribution group is expanded or unexpanded when you get it from the collection of groups returned by reading the [ContactManager.Groups](https://msdn.microsoft.com/en-us/library/jj277988\(v=office.15\)) property. If it is not expanded, you must expand it before you can get any of the contacts or nested distribution groups that it contains. Expanding a distribution group does not expand any distribution groups nested within it. You must expand each distribution group individually. If you wanted to get all contacts in the top level distribution group and all contacts in all levels of nested distribution groups, you would recursively expand nested groups and get the contacts group by group.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Caution note" alt="Caution note" /><strong>Caution</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Recursively expanding all nested distribution groups within a distribution group can result in a memory-related exception if many large distribution groups are nested within a distribution group or there are many levels of nesting. It is better to expand one level of nested group at a time and show the results of that expansion in your UI. A user can choose to expand deeper nesting levels selectively, thereby reducing the risk of a memory exception.</p></td>
</tr>
</tbody>
</table>

A Lync distribution group is a type of contact group and inherits the base [Microsoft.Lync.Model.Group.Group](https://msdn.microsoft.com/en-us/library/jj266012\(v=office.15\)) class although none of the base methods can be called on a distribution group. The Lync 2013 API provides the [Microsoft.Lync.Model.Group.DistributionGroup](https://msdn.microsoft.com/en-us/library/jj293432\(v=office.15\)) class to encapsulate the unique features of the distribution group. These features include the ability to expand the distribution group if it is not expanded.

The **DistributionGroup** class exposes an event for the following actions.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Event</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277365(v=office.15)">DistributionGroup.DescriptionChanged</a></p></td>
<td><p>The distribution group description changed.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277384(v=office.15)">DistributionGroup.ExpansionStateChanged</a></p></td>
<td><p>The distribution group has been expanded.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj274804(v=office.15)">DistributionGroup.NestedGroupAdded</a></p></td>
<td><p>A nested distribution group has been added as a member of the group raising the event.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267997(v=office.15)">DistributionGroup.NestedGroupRemoved</a></p></td>
<td><p>A nested distribution group has been removed as a member of the group raising the event.</p></td>
</tr>
</tbody>
</table>

The **DistributionGroup** class lets you perform the following operations.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Operation</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj274816(v=office.15)">DistributionGroup.BeginExpand</a></p></td>
<td><p>This asynchronous operation expands a distribution group to give you access to the group members. When expanded, the distribution group remains expanded.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj268237(v=office.15)">DistributionGroup.BeginGetAllMembers</a></p></td>
<td><p>This operation returns all of the contacts and distribution groups contained in a distribution group. The operation expands the group and any nested groups if unexpanded.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277921(v=office.15)">DistributionGroup.BeginGetOwner</a></p></td>
<td><p>This operation returns the owner of a distribution group as a <a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Microsoft.Lync.Model.Contact</a> object.</p></td>
</tr>
</tbody>
</table>

## Additional resources

  - [Get started with Lync contact lists](get-started-with-lync-contact-lists.md)

  - [Core concepts: Lync contact lists](core-concepts-lync-contact-lists.md)

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [Beyond the basics: Lync contact lists](beyond-the-basics-lync-contact-lists.md)

