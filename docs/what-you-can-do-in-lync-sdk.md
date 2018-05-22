---
title: What you can do in Lync SDK
TOCTitle: Lync SDK
ms:assetid: bb79df6a-b15e-490c-8671-fcf4befe61ba
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933175(v=office.15)
ms:contentKeyID: 50877314
ms.date: 07/24/2014
mtps_version: v=office.15
---

# What you can do in Lync SDK

Learn what you can do with Microsoft Lync 2013 SDK, including changing sign-in connection settings, signing in to and out of Lync 2013, publishing enhanced presence, and administering user privacy relationships.

**Last modified:** July 01, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Core SDK tasks<br />
In this section<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Core SDK tasks

The [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) class represents the SIP endpoint that can accept a set of user credentials and sign in to Microsoft Lync Server 2013. In addition, **LyncClient** can publish the signed-in user’s presence. Finally, **LyncClient** is the entry point for all further API functionality except for conversation automation. You access additional Lync 2013 API features by getting specialized feature manager class objects from properties of **LyncClient**. For example, you get a specialized contact manager by reading the [Client.ContactManager](https://msdn.microsoft.com/en-us/library/jj275688\(v=office.15\)) property to get the [Microsoft.Lync.Model.ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)) object.

## In this section

  - [How to: Create a side-by-side endpoint in Lync SDK](how-to-create-a-side-by-side-endpoint-in-lync-sdk.md)

  - [How to: Change sign-in connection settings in Lync SDK](how-to-change-sign-in-connection-settings-in-lync-sdk.md)

  - [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md)

  - [How to: Update and publish user telephone numbers in Lync SDK](how-to-update-and-publish-user-telephone-numbers-in-lync-sdk.md)

  - [How to: Administer privacy relationships between Lync users](how-to-administer-privacy-relationships-between-lync-users.md)

## Additional resources

  - [How do I in Lync 2013 SDK](how-do-i-in-lync-2013-sdk.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

  - [What you can do with Lync meetings](what-you-can-do-with-lync-meetings.md)

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

  - [What you can do with desktop, application, and display sharing](what-you-can-do-with-desktop-application-and-display-sharing.md)

  - [What you can do with content sharing](what-you-can-do-with-content-sharing.md)

