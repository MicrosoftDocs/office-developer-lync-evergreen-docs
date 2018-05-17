---
title: Get started with Lync contact lists
TOCTitle: Lync contact lists
ms:assetid: 3b289224-a055-4138-ba7c-f665920949d5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937302(v=office.15)
ms:contentKeyID: 50877130
ms.date: 02/11/2016
mtps_version: v=office.15
---

# Get started with Lync contact lists

Learn the programming concepts and Microsoft Lync 2013 SDK object model for building a Microsoft Lync 2013 contact list in an application UI.


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
What is a Lync contact list?  
Get started with Lync contact lists  
What can you do with a Lync contact list?  
Beyond the basics: Learn more about Lync contact lists  
Additional resources  

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="get-started-with-lync-contact-lists.md" class="uri">get-started-with-lync-contact-lists.md</a>   <a href="get-started-with-lync-contact-lists.md" class="uri">get-started-with-lync-contact-lists.md</a>   <a href="get-started-with-lync-contact-lists.md" class="uri">get-started-with-lync-contact-lists.md</a></p></td>
</tr>
</tbody>
</table>


## What is a Lync contact list?

Microsoft Lync 2013 SDK provides programmatic access to the Lync 2013 contact list object model under the contact list that is displayed in the Lync 2013 client when a user signs in to Lync. The contact list object model exposes classes, methods, properties, and events that let you do simple tasks such as updating the client contact list by adding a new contact or renaming a custom group. If your application requirements include showing a view of the Lync contact list within your own UI, you can build and maintain that list by using the contact list object model. An example of this is an application that replaces the Lync UI that is configured for UI-suppression mode. For more information, see [UI suppression](ui-suppression.md).

## Get started with Lync contact lists

The prerequisites for working with Lync contact lists are as follows:

  - Microsoft Lync 2013

  - Visual Studio 2010 or Visual Studio 2012

  - Microsoft Lync 2013 SDK

### Lync contact list essentials

To understand how to work with Lync contact lists, it is important to become familiar with the concepts in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concept</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-contact-groups.md">Lync contact groups</a></p></td>
<td><p>Learn about the custom Lync contact group and about the classes and events in Microsoft Lync 2013 SDK that give you programmatic access to the custom group.</p></td>
</tr>
<tr class="even">
<td><p><a href="distribution-groups.md">Distribution groups</a></p></td>
<td><p>Learn about the Lync distribution group and about the classes and events in Microsoft Lync 2013 SDK that let you programmatically iterate on the contacts and any nested distribution groups.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-contacts.md">Lync contacts</a></p></td>
<td><p>Learn about the Microsoft Lync 2013 classes and enumerations that encapsulate all the attributes of a Lync 2013 contact.</p></td>
</tr>
</tbody>
</table>


## What can you do with a Lync contact list?

The following table lists basic tasks for working with Lync contact lists.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Task</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="how-to-add-or-remove-a-person-from-a-contact-list.md">How to: Add or remove a person from a contact list</a></p></td>
<td><p>Shows how to remove a contact from a Lync 2013 user’s contact list by calling methods from the Lync 2013 API.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-add-rename-or-remove-a-custom-group.md">How to: Add, rename, or remove a custom group</a></p></td>
<td><p>Shows how to add or remove a custom group from a user’s contact list in Lync 2013 by using Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-move-or-copy-a-contact-between-custom-groups-in-lync-sdk.md">How to: Move or copy a contact between custom groups in Lync SDK</a></p></td>
<td><p>Shows how to use Microsoft Lync 2013 SDK to programmatically move or copy a Lync 2013 contact from one Lync 2013 group to another Lync 2013 group in a user’s contact list.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-display-a-contact-list.md">How to: Display a contact list</a></p></td>
<td><p>Shows how to use members of the <a href="microsoft-lync-model-namespace.md">Microsoft.Lync.Model</a> namespace to provide contact presence and presence updates to build a custom Lync contact list UI.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj933159(v=office.15)">How to: Search for a contact or distribution group</a></p></td>
<td><p>Shows how to search for Lync users and distribution groups by using Microsoft Lync 2013 SDK to programmatically add a contact and group feature to your code.</p></td>
</tr>
</tbody>
</table>


## Beyond the basics: Learn more about Lync contact lists

The following table lists advanced concepts for working with Lync contact lists.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concept</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="advanced-contact-search.md">Advanced contact search</a></p></td>
<td><p>Learn about custom Lync contact searches.</p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>


## Additional resources

  - [Get started with Lync 2013 SDK](get-started-with-lync-2013-sdk.md)

  - [Core concepts: Lync contact lists](core-concepts-lync-contact-lists.md)

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [Beyond the basics: Lync contact lists](beyond-the-basics-lync-contact-lists.md)

