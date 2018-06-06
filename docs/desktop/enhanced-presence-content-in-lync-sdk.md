---
title: Enhanced presence content in Lync SDK
TOCTitle: Enhanced presence content
ms:assetid: 813d89b3-950e-4a20-9659-9c0fb1c47785
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933095(v=office.15)
ms:contentKeyID: 50877226
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Enhanced presence content in Lync SDK

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the components of Microsoft Lync 2013 enhanced presence and how it is implemented in Microsoft Lync 2013 SDK.

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
What is enhanced presence?<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## What is enhanced presence?

Enhanced presence is information that a client endpoint publishes on behalf of a signed-in user and displayed in the user’s Lync contact card. Presence is summarized as how available the user is for a conversation and how the user can be contacted. Simplified presence, a standard used by all IM clients, provides just the current availability of a user. For a client application that can only communicate by using an IM chat feature, this is sufficient. The Microsoft Lync 2013 client supports multi-modal communication through the SIP protocol supported by Microsoft Lync Server 2013, but also by using voice over a public switched telephone network (PSTN). With these additional communication channel options, it is necessary to enhance simple presence by providing the availability of all possible communication options so that a user can make the correct communication mode choice.

The Lync 2013 model allows a user to publish two kinds of notes that are displayed in the Lync client and accessible from the Lync 2013 API. An out-of-office (OOF) note can be published when a user is going to be away for an extended period of time. When an OOF note is not appropriate, a personal note can be published. Personal notes are normally single sentence status updates that all subscribing users see when viewing the contact card of the publishing user.

The Lync 2013 API gives the ability to both obtain the enhanced presence information published by a user and publish enhanced presence information on behalf of the local user. Before obtaining a user’s presence information, an application must inform Lync Server 2013 that the local user is interested in any enhanced presence published by another user. This is known as subscribing to enhanced presence. For information about this process, see [Presence publication and subscription in Lync SDK](presence-publication-and-subscription-in-lync-sdk.md).

## Additional resources

  - [Core concepts: Enhanced presence](core-concepts-enhanced-presence.md)

  - [Presence publication and subscription in Lync SDK](presence-publication-and-subscription-in-lync-sdk.md)

