---
title: Get started with enhanced presence in Lync SDK
TOCTitle: Enhanced presence
ms:assetid: 7fb19aad-fa7a-432c-ba6c-7e9375fdd942
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933105(v=office.15)
ms:contentKeyID: 50877238
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Get started with enhanced presence in Lync SDK

Learn the programming concepts and Microsoft Lync 2013 SDK object model for building an application that shows the enhanced presence information for any Microsoft Lync 2013 user.



**Applies to**: Lync 2013 | Lync Server 2013

 

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="get-started-with-enhanced-presence-in-lync-sdk.md" class="uri"><img src="images/JJ933215.mod_icon_getstartbox(Office.15).gif"/></a>   <a href="get-started-with-enhanced-presence-in-lync-sdk.md" class="uri"><img src="images/JJ933215.mod_icon_dobox(Office.15).gif"/></a>   <a href="get-started-with-enhanced-presence-in-lync-sdk.md" class="uri"><img src="images/JJ933215.mod_icon_startbox(Office.15).gif"/></a></p></td>
</tr>
</tbody>
</table>

## What is enhanced presence?

Enhanced presence is a superset of the presence data format defined by RFC 3261, RFC 3265, and RFC 3863. Enhanced presence is a protocol for publishing and subscribing to presence data as well as a mechanism to authorize the access of a presence subscribing user to the presence of a publishing user.

Enhanced presence is organized into the state, calendar data, contact card, device, note, options, and call routing categories. These presence categories are exposed to the Lync 2013 API developer as class objects that encapsulate the SIP XML elements described in the presence protocol.

## Get started with enhanced presence

The prerequisites for working with enhanced presence are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Enhanced presence essentials

To understand how to work with enhanced presence, it is important to become familiar with the concepts in the following table.

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
<td><p><a href="enhanced-presence-content-in-lync-sdk.md">Enhanced presence content in Lync SDK</a></p></td>
<td><p>Learn about the components of Microsoft Lync 2013 enhanced presence and how Lync 2013 user privacy relationships constrain views of presence information.</p></td>
</tr>
<tr class="even">
<td><p><a href="presence-publication-and-subscription-in-lync-sdk.md">Presence publication and subscription in Lync SDK</a></p></td>
<td><p>Learn about the concept of contact presence publication and subscription in Microsoft Lync 2013 SDK.</p></td>
</tr>
</tbody>
</table>

## What can you do with enhanced presence?

The following table lists basic tasks for working with enhanced presence.

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
<td><p><a href="how-to-get-the-enhanced-presence-of-a-lync-user.md">How to: Get the enhanced presence of a Lync user</a></p></td>
<td><p>Learn how to use Microsoft Lync 2013 SDK to get and display the enhanced presence that is published by a Microsoft Lync 2013 user.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-display-contact-information-by-using-a-contactcard-control.md">How to: Display contact information by using a ContactCard control</a></p></td>
<td><p>Learn how to use the Lync Controls ContactCard in a WPF window or Silverlight page to display contact information for a Lync user.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-get-the-communication-modes-of-a-lync-user.md">How to: Get the communication modes of a Lync user</a></p></td>
<td><p>Learn how use Microsoft Lync 2013 SDK to get the communication modalities that a Microsoft Lync 2013 user can use to participate in conversations.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-publish-enhanced-presence-information.md">How to: Publish enhanced presence information</a></p></td>
<td><p>Learn how to publish Microsoft Lync 2013 presence information such as the availability and personal note of a Lync 2013 contact by using methods in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-subscribe-to-enhanced-presence-content.md">How to: Subscribe to enhanced presence content</a></p></td>
<td><p>Learn how to use Microsoft Lync 2013 SDK to create a subscription to the enhanced presence published by a user.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-use-presence-information-in-an-application.md">How to: Use presence information in an application</a></p></td>
<td><p>Learn how to use the presence information published by a Microsoft Lync 2013 contact to make an application more responsive to changes in a user’s willingness to communicate and ability to communicate in specific modes.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-display-and-publish-custom-availability-in-lync-sdk.md">How to: Display and publish custom availability in Lync SDK</a></p></td>
<td><p>Learn how to display and publish custom Microsoft Lync 2013 presence in an application by using Microsoft Lync 2013 SDK.</p></td>
</tr>
</tbody>
</table>

## Beyond the basics: Learn more about enhanced presence

The following table lists advanced concepts for working with enhanced presence.

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
<td><p><a href="contact-privacy-relationship-administration.md">Contact privacy relationship administration</a></p></td>
<td><p>Learn how Microsoft Lync 2013 user privacy relationships constrain a Lync 2013 user’s view of another Lync 2013 user’s published presence.</p></td>
</tr>
<tr class="even">
<td><p><a href="custom-presence-states.md">Custom presence states</a></p></td>
<td><p>Learn about the concept of localizing a Microsoft Lync 2013 API-enabled application by showing custom user activity strings instead of the default activity strings that are included with an installation of Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Get started with Lync 2013 SDK](get-started-with-lync-2013-sdk.md)

  - [Core concepts: Enhanced presence](core-concepts-enhanced-presence.md)

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

  - [Beyond the basics: Enhanced presence](beyond-the-basics-enhanced-presence.md)

