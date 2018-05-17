---
title: Lync contacts
TOCTitle: Lync contacts
ms:assetid: 3e060b5f-0aa8-4e91-8ff7-e721fc6045f0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937300(v=office.15)
ms:contentKeyID: 50877125
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Lync contacts

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the Microsoft Lync 2013 classes and enumerations that encapsulate all of the attributes of a Lync 2013 contact.


_**Applies to:** Lync 2013 | Lync Server 2013_

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


> [!NOTE]
> <P>The API entry point for a conversation in the Microsoft Lync 2013 API is the <A href="conversation-class-microsoft-lync-model-conversation_2.md">Conversation</A> object. Users or telephone numbers that will be the remote participants in a conversation are always represented by <A href="contact-class-microsoft-lync-model_2.md">Contact</A> objects. You cannot start a conversation in Lync 2013 without a contact.</P>



### GetContactByUri method

In addition to being the SIP URI of a Lync 2013 user, a [Contact](contact-class-microsoft-lync-model_2.md) object can be a telephone number or a Hotmail account. As long as you have a valid SIP, TEL, or mail URI, you can find a **Contact** object by calling the [GetContactByUri](contactmanager-getcontactbyuri-method-microsoft-lync-model_2.md) method. It is important to understand that the URI that you provide must be resolved to an entity that publishes its presence in order to see the availability of the contact. For example, if you supply a mail URI, the availability of the mail contact will always show as unknown because a mail account cannot communicate in real-time and does not publish presence. A public switch telephone network (PSTN) telephone number represented by a TEL URI is always available to respond to audio calls in real time but does not publish availability including the ability to accept calls.

### Finding contacts by using the search feature of the API

If you must use **Contact** objects that are guaranteed to resolve to entities that publish presence, then use the Lync 2013 search feature to return a set of **Contact** objects that belong to the local Microsoft Lync Server 2013 topology or a federated topology. Contacts found by the search feature have the full presence publishing capability necessary to get real-time updates of availability, willingness to communicate, and communication capabilities. For information about searching for contacts, see [How to: Search for a contact or distribution group in Lync SDK](https://msdn.microsoft.com/en-us/library/jj933159\(v=office.15\)).

## Features of a contact

The [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) class and related classes encapsulate the following features.

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
<td><p><a href="contact-class-microsoft-lync-model_2.md">Contact</a></p></td>
<td><p>The contact.</p></td>
</tr>
<tr class="even">
<td><p><a href="contacttype-enumeration-microsoft-lync-model_2.md">ContactType</a></p></td>
<td><p>The kind of contact. A contact is typically a person but can be an automated attendant, a bot, or a hunt group.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactavailability-enumeration-microsoft-lync-model_2.md">ContactAvailability</a></p></td>
<td><p>Contact availability. Enumerates the ways or &quot;states&quot; in which a contact is available for a conversation. Availability states range from offline through free to have a conversation. Intermediate states include busy and do-not-disturb.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcalendarstate-enumeration-microsoft-lync-model_2.md">ContactCalendarState</a></p></td>
<td><p>Contact calendar state. Enumerates the scheduled activity states that contacts can add to their Microsoft Outlook calendar. These time and date based calendar states are aggregated with the contact availability states that are published by the contact to present a complete view of the contact’s availability.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactcapabilities-enumeration-microsoft-lync-model_2.md">ContactCapabilities</a></p></td>
<td><p>Contact conversation mode capabilities. Enumerates the modes in which a contact can participate in a conversation. These capabilities are published by a contact when a capability changes. For example, if a contact is available only through a mobile phone, the collection of contact capabilities does not include a capability enumerated by <a href="https://msdn.microsoft.com/en-us/library/gg253131(v=office.15)">CaptureInstantMessage</a> or <a href="https://msdn.microsoft.com/en-us/library/gg253131(v=office.15)">RenderInstantMessage</a>.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactendpoint-class-microsoft-lync-model_2.md">ContactEndpoint</a></p></td>
<td><p>Contact endpoints. Represents a device on which a contact can be available. These devices include telephone numbers and the Lync client. For example, the collection of a contact’s endpoints can include a mobile phone number that is enumerated by <a href="https://msdn.microsoft.com/en-us/library/gg254732(v=office.15)">MobilePhone</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactinformationchangedeventargs-class-microsoft-lync-model_2.md">ContactInformationChangedEventArgs</a></p></td>
<td><p>Contact information change notification. As a contact signs in and out of an endpoint, goes into or out of a meeting, updates a contact card detail, or other activity, these activities are published to any person who has subscribed to such publications. Contact subscription is handled on the Lync client or on your custom application. These publication events are presented in your application as <a href="contact-contactinformationchanged-event-microsoft-lync-model_2.md">ContactInformationChanged</a> events. <a href="contactinformationchangedeventargs-class-microsoft-lync-model_2.md">ContactInformationChangedEventArgs</a> exposes a property that returns a collection of <a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a> instances, which is a list of all of the contact information items in the publication that caused the event to be raised on a subscribing client.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a></p></td>
<td><p>Contact information types. Enumerates the kinds of information that a contact can publish at any time.</p></td>
</tr>
<tr class="odd">
<td><p><a href="publishablecontactinformationtype-enumeration-microsoft-lync-model_2.md">PublishableContactInformationType</a></p></td>
<td><p>Client-publishable contact information types. Enumerates the kinds of contact information that can be published from a Microsoft Lync 2013 API-based client. This enumeration of information types is much smaller than the enumeration of information types that can be published from Microsoft Lync Server 2013. The server publishes on behalf of a contact when elements of a contact card are changed in a data source such as Active Directory Domain Services.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactmanager-class-microsoft-lync-model_2.md">ContactManager</a></p></td>
<td><p>Contact list manager. The contact manager lets you manage a user’s contact list as it appears in the Lync 2013 client and your own custom client. Use the contact manager to search for contacts and groups that are not in the contact list, add contacts or a distribution group, rename custom groups, add new custom groups, or remove a custom group. If you have the telephone number or URI of a person, you can use the contact manager to return a <a href="contact-class-microsoft-lync-model_2.md">Contact</a> instance representing the person.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactsetting-enumeration-microsoft-lync-model_2.md">ContactSetting</a></p></td>
<td><p>Local contact settings. These settings effect how a local signed-in user interacts with any contact. The settings are only visible to the local user and do not affect the person represented by the contact. There is one exception to this rule. The <a href="https://msdn.microsoft.com/en-us/library/gg253709(v=office.15)">AccessLevel</a> setting restricts the contact information that another subscribing contact can see about the local signed-in user. For example, if Jeff Hay signs in to Lync as the local user, he can change a contact setting on the contact that represents Daniel Roth so that Daniel can only see Jeff’s contact card information that is appropriate for a PIC user.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactsettingchangedeventargs-class-microsoft-lync-model_2.md">ContactSettingChangedEventArgs</a></p></td>
<td><p>Represents the contact settings that were changed as a result of a contact setting changed event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactsourcetypes-enumeration-microsoft-lync-model_2.md">ContactSourceTypes</a></p></td>
<td><p>Enumerates the contact provider type. This enumeration has a FlagsAttribute attribute that allows a bitwise combination of its member values.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactsubscription-class-microsoft-lync-model_2.md">ContactSubscription</a></p></td>
<td><p>Specifies the type of contact information to be subscribed on a collection of contacts set in the subscription.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactsubscriptionrefreshrate-enumeration-microsoft-lync-model_2.md">ContactSubscriptionRefreshRate</a></p></td>
<td><p>Enumerates contact subscription freshness.</p></td>
</tr>
</tbody>
</table>


## Additional resources

  - [How to: Search for a contact, distribution group, or chat room](https://msdn.microsoft.com/en-us/library/jj933159\(v=office.15\))

  - [Get started with Lync contact lists](get-started-with-lync-contact-lists.md)

  - [Core concepts: Lync contact lists](core-concepts-lync-contact-lists.md)

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [Beyond the basics: Lync contact lists](beyond-the-basics-lync-contact-lists.md)

