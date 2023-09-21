---
title: Lync contact groups
TOCTitle: Lync contact groups
ms:assetid: 6592af78-d163-4f46-9774-44fc4febf36c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933068(v=office.15)
ms:contentKeyID: 50877198
ms.date: 07/24/2014
mtps_version: v=office.15
description: Master Microsoft Lync 2013 contact groups with our comprehensive guide. Learn about SDK classes, events, and gain programmatic access to custom groups.
---

# Lync contact groups

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about Lync Microsoft Lync 2013 contact groups and the Microsoft Lync 2013 SDK classes and events that give you programmatic access to the custom group.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Contact groups<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Contact groups

A Lync 2013 contact group is collections of contacts and is simply a logical grouping of SIP URIs that resolve to people. Among the group types is the custom group, which is an arbitrary and user-defined collection. The distribution group is an exception to this rule as it is defined once in Active Directory and can be displayed in a contact list, but not changed in the contact list. A logical group such as a custom group can include any user or telephone number that can be resolved to a SIP or TEL URI. This means that a logical group can include organization Lync users, federated users on another Microsoft Lync Server 2013 topology, or federated users on a SIP server such as Yahoo or Windows Live Messenger.

A Lync 2013 typical group collection includes multiple custom groups, a single Frequent Contacts group, a single Favorite Contacts group, and can include one or more distribution groups. Each of these group types has its own set of rules that govern group operations. For example, you can rename a custom group while you cannot rename any of the other group types. Despite these behavioral differences, all of the group subtypes inherit a base [Microsoft.Lync.Model.Group.Group](https://msdn.microsoft.com/library/jj266012\(v=office.15\)) class and inherit all of the public properties, events, and methods of the base group. Although it is syntactically correct to call the [Group.BeginRemoveContact](https://msdn.microsoft.com/library/jj268196\(v=office.15\)) on a [Microsoft.Lync.Model.Group.DistributionGroup](https://msdn.microsoft.com/library/jj293432\(v=office.15\)) object, this operation is not allowed and results in an exception. Other unique characteristics of the group subtypes are implemented in the group subclasses. For example, only the custom group can be renamed, so the [Microsoft.Lync.Model.Group.CustomGroup](https://msdn.microsoft.com/library/jj277245\(v=office.15\)) class has a rename method but the other group subclasses do not.

The [Microsoft.Lync.Model.ContactManager](https://msdn.microsoft.com/library/jj266459\(v=office.15\)) exposes group-related methods that allow you to add or remove groups. These methods apply only to custom groups because you cannot add or remove any other type of group. However, the [ContactManager.BeginRemoveGroup](https://msdn.microsoft.com/library/jj278089\(v=office.15\)) method accepts any class that inherits the **Group** base class. It is syntactically correct to write application logic that passes a distribution group, Favorite Contacts, or Frequent Contacts group to this method. At runtime, this code generates an **ArgumentException** and the group is not removed.

The **ContactManager** exposes two methods for adding groups.

A custom contact group is a group that your application has full programmatic control over. You can create a new custom group, delete a custom group, rename a custom group, and change the group membership. In contrast, you cannot rename or remove a distribution group or the FavoriteContacts and FrequentContacts groups. All of these specialty group types are subtypes of the [Microsoft.Lync.Model.Group.Group](https://msdn.microsoft.com/library/jj266012\(v=office.15\)) class and inherit all of the public properties, events, and methods of the base group.

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
<td><p>The Lync client contact list displays a contact group under the title &quot;Frequent contacts.&quot; The corresponding API classes are the <a href="https://msdn.microsoft.com/library/jj277579(v=office.15)">Microsoft.Lync.Model.Group.FavoriteContacts</a> and <a href="https://msdn.microsoft.com/library/jj275307(v=office.15)">Microsoft.Lync.Model.Group.FrequentContacts</a> groups. Because the API exposes the frequent contacts as these two subgroups, you can show them as separate groups in a custom contact list. The <a href="https://msdn.microsoft.com/library/jj278363(v=office.15)">Group.Name</a> property value for this group is &quot;Pinned Contacts&quot; and the FrequentContacts group name property is &quot;Most Used Contacts.&quot;</p></td>
</tr>
</tbody>
</table>

## See also

  - [Get started with Lync contact lists](get-started-with-lync-contact-lists.md)

  - [Core concepts: Lync contact lists](core-concepts-lync-contact-lists.md)

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [Beyond the basics: Lync contact lists](beyond-the-basics-lync-contact-lists.md)

