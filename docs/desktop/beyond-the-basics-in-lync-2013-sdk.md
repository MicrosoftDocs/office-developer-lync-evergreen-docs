---
title: Beyond the basics in Lync 2013 SDK
TOCTitle: Beyond the basics
ms:assetid: ff41897b-443f-42c3-8180-0e9ad33cd4e5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933259(v=office.15)
ms:contentKeyID: 50877405
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Beyond the basics in Lync 2013 SDK

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the advanced features of Microsoft Lync 2013 SDK that you can use to make your stand-alone Lync 2013 API-enabled application more flexible and robust.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Advanced API features<br />
In this section<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Advanced API features

These advanced features are designed to give you programmatic access to some of the options that a Lync user can access through the **Lync options** menu on the client. If you are building an application that replaces the UI of a UI-suppressed Lync 2013 client and you want to provide a user with configuration options, then the topics in this section will get you started.

UI suppression is a feature that starts the Lync.exe process programmatically from your application and suppresses the entire user interface of the Lync 2013 client. This means that a user can only access Lync contacts, change configuration settings, start and accept conversations, and participate in conversations through your application.

Sign-in configuration means giving a user the ability to set connection settings. Settings include selecting automatic configuration or manual configuration, setting internal and external sign-in server names and IP addresses, and setting the connection protocol. These settings are also found in the **Lync options, Personal, Advanced Connection Settings** dialog box.

Conversation alert settings give a user the ability to control the circumstances when a conversation invitation alert dialog box open on the primary display. With these settings, the user can set the type and priority of conversation invitation that opens the invitation dialog box.

## In this section

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Topic</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="beyond-the-basics-lync-2013-sdk.md">Beyond the basics: Lync 2013 SDK</a></p></td>
<td><p>Learn about advanced concepts such as UI suppression, sign-in settings, and telephone number administration in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="beyond-the-basics-lync-controls.md">Beyond the basics: Lync Controls</a></p></td>
<td><p>Learn about advanced features of the Microsoft Lync 2013 Controls that you can use to make your stand-alone Lync 2013 API-enabled application more flexible and robust.</p></td>
</tr>
<tr class="odd">
<td><p><a href="beyond-the-basics-enhanced-presence.md">Beyond the basics: Enhanced presence</a></p></td>
<td><p>Learn about advanced enhanced presence concepts such as Lync 2013 contact privacy relationship administration and custom presence states in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="beyond-the-basics-lync-contact-lists.md">Beyond the basics: Lync contact lists</a></p></td>
<td><p>Learn about advanced features of Microsoft Lync 2013 SDK that you can use to give your custom Lync 2013 contact list advanced capabilities such as contact searching and distribution group expansion.</p></td>
</tr>
<tr class="odd">
<td><p><a href="beyond-the-basics-lync-conversations.md">Beyond the basics: Lync conversations</a></p></td>
<td><p>Learn about extending the functionality of the Lync 2013 conversation window by creating hosted Silverlight browser applications that are powered by Microsoft Lync 2013 SDK object model to tightly integrate the browser application with the hosting Lync conversation window.</p></td>
</tr>
<tr class="even">
<td><p><a href="beyond-the-basics-lync-meetings.md">Beyond the basics: Lync meetings</a></p></td>
<td><p>Learn about obtaining meeting admission keys for external access, managing the lobby of a meeting, and pinning or locking the video stream of a meeting participant.</p></td>
</tr>
<tr class="odd">
<td><p><a href="beyond-the-basics-persistent-chat.md">Beyond the basics: Persistent Chat</a></p></td>
<td><p>Learn about advanced features of Microsoft Lync 2013 SDK that let you enhance the Persistent Chat experience of the Lync 2013 user.</p></td>
</tr>
<tr class="even">
<td><p><a href="beyond-the-basics-desktop-application-and-display-sharing.md">Beyond the basics: Desktop, application, and display sharing</a></p></td>
<td><p>Learn about advanced features of Microsoft Lync 2013 SDK that let you complete the resource sharing experience of the Lync 2013 user in your application.</p></td>
</tr>
<tr class="odd">
<td><p><a href="beyond-the-basics-content-sharing.md">Beyond the basics: Content sharing</a></p></td>
<td><p>Learn about using Microsoft Lync 2013 SDK to handle meeting content sharing events and shared content item presentation in Lync 2013 meetings.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Get started with Lync 2013 SDK](get-started-with-lync-2013-sdk.md)

  - [Core concepts: Lync 2013 SDK](core-concepts-lync-2013-sdk.md)

  - [What you can do in Lync SDK](what-you-can-do-in-lync-sdk.md)

