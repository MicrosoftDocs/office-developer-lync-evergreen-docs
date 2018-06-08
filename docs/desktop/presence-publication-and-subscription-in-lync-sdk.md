---
title: Presence publication and subscription in Lync SDK
TOCTitle: Presence publication and subscription
ms:assetid: e9dc2b21-fdef-4fe3-bc02-8a8bd2204635
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933247(v=office.15)
ms:contentKeyID: 50877393
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Presence publication and subscription in Lync SDK

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the concept of contact presence publication and subscription in Microsoft Lync 2013 SDK.

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
What is presence?<br />
Presence subscription<br />
Presence publication<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## What is presence?

In its simple form, presence expresses the availability and willingness of a person to join a conversation by using a SIP client such as Microsoft Lync 2013. Any user of such a client must make his or her presence available to any other user who might want to communicate. This is known as presence publication. The users who are interested in these presence publications are known as presence subscribers.

Availability or willingness to communicate changes over time; for example, when the user goes into a meeting and cannot join new IM conversations. Users should publish updates to their presence that shows they are in a meeting and cannot join an IM conversation. Microsoft Lync 2013 improves this simple presence by letting a user publish additional information such as other ways to contact the user, their working and daily calendars, and personal and out of office notes.

## Presence subscription

Presence subscription is an operation that lets the Lync 2013 client know which people that you are interested in seeing refreshed presence information from and what aspect of their enhanced presence you are interested in. When your application creates a presence subscription for a set of users and a set of enhanced presence information, the Lync 2013 client platform raises events to tell you that one of the users in the set has published updated presence information in the set of information that you are interested in. The presence subscription operation is encapsulated by the [Microsoft.Lync.Model.ContactSubscription](https://msdn.microsoft.com/en-us/library/jj268195\(v=office.15\)) class. Create a new **ContactSubscription** by calling the [ContactManager.CreateSubscription](https://msdn.microsoft.com/en-us/library/jj267359\(v=office.15\)) method.

The user who is signed in to the Lync 2013 client defines the set of subscribed users by adding people to the client contact list. Your custom application should not use the client-created subscription for presence events.

Earlier versions of Lync created a subscription for all contacts in the user’s contact list. This client subscription was maintained for all contacts even when a subscribed contact was scrolled out of view in the contact list UI. For this reason, it was not necessary to subscribe to any contact that you could obtain by iterating on the [ContactManager.Groups](https://msdn.microsoft.com/en-us/library/jj277988\(v=office.15\)) property group collection. To improve performance, Lync 2013 maintains subscriptions only for the contacts that are scrolled into view on the UI and removes out-of-view contacts from the subscription.

If your application relies on a client-based subscription, you should assume that the contact whose presence updates that you want is not in the current client subscription. The Lync 2013 API does not let you examine the subscription created by the Lync 2013 client. For this reason, you cannot determine programmatically whether a contact is in the client subscription. Instead, your application should create a new subscription and add all contacts that are to be displayed on your application UI to the subscription. Doing so ensures that all interested contacts are subscribed to.

For information about how to create a contact subscription, see [How to: Subscribe to enhanced presence content](how-to-subscribe-to-enhanced-presence-content.md).

## Presence publication

Presence publication is the publishing of the local signed-in user’s enhanced presence information for the use of other users who have subscribed to this presence. Your application can set the presence of the local signed-in user to such availability as available, busy, do not disturb, be right back, off work, or appear away. These programmatically set availability values are overridden by the Lync 2013 client when the local user has not touched the keyboard or mouse for some time. For example, the availability of available is set but the user is physically away from the computer. The client overrides that availability with an availability of away. The user’s personal note, out of office note, and telephone numbers can also be published. For information about publishing presence, see [How to: Publish enhanced presence information](how-to-publish-enhanced-presence-information.md).

The information that is published programmatically is immediately available to all subscribing users. An application can control which published enhanced presence information is available to subscribing users by modifying the default privacy relationship assigned to each subscribing contact. For information about how to set privacy relationships, see [How to: Administer privacy relationships between Lync users](how-to-administer-privacy-relationships-between-lync-users.md).

## See also

  - [Enhanced presence content in Lync SDK](enhanced-presence-content-in-lync-sdk.md)

  - [How to: Display a contact list](how-to-display-a-contact-list.md)

  - [How to: Start a Lync IM conversation](how-to-start-a-lync-im-conversation.md)

