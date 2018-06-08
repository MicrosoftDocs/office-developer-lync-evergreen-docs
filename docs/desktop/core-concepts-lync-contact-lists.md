---
title: 'Core concepts: Lync contact lists'
TOCTitle: Lync contact lists
ms:assetid: 1c93bc2a-c228-497f-8b2c-62a5fa7f24b2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937275(v=office.15)
ms:contentKeyID: 50877093
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Core concepts: Lync contact lists

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the concepts that you need to know before you use the contact-related object model of Microsoft Lync 2013 SDK to modify a user’s contact list in Microsoft Lync 2013 or create your own Lync contact list in an application.

**Last modified:** February 22, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Contact list overview<br />
Contact list object model<br />
In this section<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Contact list overview

The Lync platform provides a contact manager class that lets you manage the contact list that is displayed in the Lync 2013 UI. Contact list management tasks that you can do programmatically include adding and removing contacts, adding and removing custom groups, renaming custom groups, and changing the membership of custom groups. In addition to contact list management, the contact manager gives you access to individual contact and group objects that you can use to create new conversations and invite users or groups of users.

## Contact list object model

The object model mirrors the contact list elements that are shown in the Lync 2013 UI as shown in figure 1. You can use the Lync 2013 API to programmatically search for contacts and obtain the same results that a user obtains by typing contact names, group names, or skill keywords in the contact/group search feature of the UI. The [Microsoft.Lync.Model.Group.FavoriteContacts](https://msdn.microsoft.com/en-us/library/jj277579\(v=office.15\)) object encapsulates the favorite contacts element of the list on the UI. You can move contacts in to and out of the favorite contacts group programmatically. Custom groups can be created or removed programmatically. You can also add or remove contacts from the custom groups.

Figure 1 shows the Lync 2013 client with the programmable contact list features called out. To add these features to an application, you should be familiar with the contact list objects described in this section.

Figure 1. Lync 2013 client contact list with programmable components called out

  
![Lync 2013 client with contact list elements named](images/JJ937275.LyncClientSDK_LyncContactList(Office.15).jpg "Lync 2013 client with contact list elements named")

## In this section

  - [Lync contact groups](lync-contact-groups.md)

  - [Distribution groups](distribution-groups.md)

  - [Lync contacts](lync-contacts.md)

## See also

  - [Get started with Lync contact lists](get-started-with-lync-contact-lists.md)

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [Beyond the basics: Lync contact lists](beyond-the-basics-lync-contact-lists.md)

