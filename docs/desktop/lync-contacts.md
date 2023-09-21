---
title: Lync contacts
TOCTitle: Lync contacts
ms:assetid: 3e060b5f-0aa8-4e91-8ff7-e721fc6045f0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937300(v=office.15)
ms:contentKeyID: 50877125
ms.date: 07/24/2014
mtps_version: v=office.15
description: Master Microsoft Lync 2013 with our comprehensive guide. Learn about contact attributes, finding contacts, and more. Perfect for Lync Server 2013 users.
---

# Lync contacts

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the Microsoft Lync 2013 classes and enumerations that encapsulate all of the attributes of a Lync 2013 contact.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p>
<p><strong>In this article</strong><br />
Finding contacts<br />
Features of a contact<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Finding contacts

A contact is a person who can sign in to Lync 2013 or another public IM connectivity (PIC) client. The modalities with which a Lync 2013 user can communicate with another contact depend on the type of client on which the other contact is signed in. A PIC client such as Windows Live Messenger or the AOL client can communicate with a Lync 2013 client by using the IM modality only.

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
<td><p>The API entry point for a conversation in the Microsoft Lync 2013 API is the <a href="https://msdn.microsoft.com/en-us/library/jj276988(v=office.15)">Conversation</a> object. Users or telephone numbers that will be the remote participants in a conversation are always represented by <a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Contact</a> objects. You cannot start a conversation in Lync 2013 without a contact.</p></td>
</tr>
</tbody>
</table>

### GetContactByUri method

In addition to being the SIP URI of a Lync 2013 user, a [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object can be a telephone number or a Hotmail account. As long as you have a valid SIP, TEL, or mail URI, you can find a **Contact** object by calling the [GetContactByUri](https://msdn.microsoft.com/en-us/library/jj274481\(v=office.15\)) method. It is important to understand that the URI that you provide must be resolved to an entity that publishes its presence in order to see the availability of the contact. For example, if you supply a mail URI, the availability of the mail contact will always show as unknown because a mail account cannot communicate in real-time and does not publish presence. A public switch telephone network (PSTN) telephone number represented by a TEL URI is always available to respond to audio calls in real time but does not publish availability including the ability to accept calls.

### Finding contacts by using the search feature of the API

If you must use **Contact** objects that are guaranteed to resolve to entities that publish presence, then use the Lync 2013 search feature to return a set of **Contact** objects that belong to the local Microsoft Lync Server 2013 topology or a federated topology. Contacts found by the search feature have the full presence publishing capability necessary to get real-time updates of availability, willingness to communicate, and communication capabilities. For information about searching for contacts, see [How to: Search for a contact or distribution group in Lync SDK](https://msdn.microsoft.com/en-us/library/jj933159\(v=office.15\)).

## Features of a contact

The [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) class and related classes encapsulate the following features.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Class/enumeration</p></th>
<th><p>Features and attributes</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Contact</a></p></td>
<td><p>The contact.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277831(v=office.15)">ContactType</a></p></td>
<td><p>The kind of contact. A contact is typically a person but can be an automated attendant, a bot, or a hunt group.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293978(v=office.15)">ContactAvailability</a></p></td>
<td><p>Contact availability. Enumerates the ways or &quot;states&quot; in which a contact is available for a conversation. Availability states range from offline through free to have a conversation. Intermediate states include busy and do-not-disturb.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267651(v=office.15)">ContactCalendarState</a></p></td>
<td><p>Contact calendar state. Enumerates the scheduled activity states that contacts can add to their Microsoft Outlook calendar. These time and date based calendar states are aggregated with the contact availability states that are published by the contact to present a complete view of the contact’s availability.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266456(v=office.15)">ContactCapabilities</a></p></td>
<td><p>Contact conversation mode capabilities. Enumerates the modes in which a contact can participate in a conversation. These capabilities are published by a contact when a capability changes. For example, if a contact is available only through a mobile phone, the collection of contact capabilities does not include a capability enumerated by CaptureInstantMessage or RenderInstantMessage.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276722(v=office.15)">ContactEndpoint</a></p></td>
<td><p>Contact endpoints. Represents a device on which a contact can be available. These devices include telephone numbers and the Lync client. For example, the collection of a contact’s endpoints can include a mobile phone number that is enumerated by MobilePhone.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266428(v=office.15)">ContactInformationChangedEventArgs</a></p></td>
<td><p>Contact information change notification. As a contact signs in and out of an endpoint, goes into or out of a meeting, updates a contact card detail, or other activity, these activities are published to any person who has subscribed to such publications. Contact subscription is handled on the Lync client or on your custom application. These publication events are presented in your application as <a href="https://msdn.microsoft.com/en-us/library/jj275543(v=office.15)">ContactInformationChanged</a> events. <a href="https://msdn.microsoft.com/en-us/library/jj266428(v=office.15)">ContactInformationChangedEventArgs</a> exposes a property that returns a collection of <a href="https://msdn.microsoft.com/en-us/library/jj277212(v=office.15)">ContactInformationType</a> instances, which is a list of all of the contact information items in the publication that caused the event to be raised on a subscribing client.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277212(v=office.15)">ContactInformationType</a></p></td>
<td><p>Contact information types. Enumerates the kinds of information that a contact can publish at any time.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293821(v=office.15)">PublishableContactInformationType</a></p></td>
<td><p>Client-publishable contact information types. Enumerates the kinds of contact information that can be published from a Microsoft Lync 2013 API-based client. This enumeration of information types is much smaller than the enumeration of information types that can be published from Microsoft Lync Server 2013. The server publishes on behalf of a contact when elements of a contact card are changed in a data source such as Active Directory Domain Services.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266459(v=office.15)">ContactManager</a></p></td>
<td><p>Contact list manager. The contact manager lets you manage a user’s contact list as it appears in the Lync 2013 client and your own custom client. Use the contact manager to search for contacts and groups that are not in the contact list, add contacts or a distribution group, rename custom groups, add new custom groups, or remove a custom group. If you have the telephone number or URI of a person, you can use the contact manager to return a <a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Contact</a> instance representing the person.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267670(v=office.15)">ContactSetting</a></p></td>
<td><p>Local contact settings. These settings effect how a local signed-in user interacts with any contact. The settings are only visible to the local user and do not affect the person represented by the contact. There is one exception to this rule. The AccessLevel  setting restricts the contact information that another subscribing contact can see about the local signed-in user. For example, if Jeff Hay signs in to Lync as the local user, he can change a contact setting on the contact that represents Daniel Roth so that Daniel can only see Jeff’s contact card information that is appropriate for a PIC user.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277406(v=office.15)">ContactSettingChangedEventArgs</a></p></td>
<td><p>Represents the contact settings that were changed as a result of a contact setting changed event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276535(v=office.15)">ContactSourceTypes</a></p></td>
<td><p>Enumerates the contact provider type. This enumeration has a FlagsAttribute attribute that allows a bitwise combination of its member values.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj268195(v=office.15)">ContactSubscription</a></p></td>
<td><p>Specifies the type of contact information to be subscribed on a collection of contacts set in the subscription.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275273(v=office.15)">ContactSubscriptionRefreshRate</a></p></td>
<td><p>Enumerates contact subscription freshness.</p></td>
</tr>
</tbody>
</table>

## See also

  - [How to: Search for a contact, distribution group, or chat room](https://msdn.microsoft.com/en-us/library/jj933159\(v=office.15\))

  - [Get started with Lync contact lists](get-started-with-lync-contact-lists.md)

  - [Core concepts: Lync contact lists](core-concepts-lync-contact-lists.md)

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [Beyond the basics: Lync contact lists](beyond-the-basics-lync-contact-lists.md)

