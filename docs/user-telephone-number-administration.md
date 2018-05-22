---
title: User telephone number administration
TOCTitle: User telephone number administration
ms:assetid: 7d832dc3-0913-4382-9213-21697f0fac48
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933103(v=office.15)
ms:contentKeyID: 50877236
ms.date: 07/24/2014
mtps_version: v=office.15
---

# User telephone number administration

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the capabilities of the Lync 2013 API to let your application manage a Lync 2013 user’s telephone list, which includes adding a telephone number, changing a telephone number, publishing a telephone number on the contact card, and removing a number from the contact card.

**Last modified:** January 07, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Lync telephone list administration<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Lync telephone list administration

Lync defines a set of four telephone number types that a user can add corresponding telephone numbers to. The Lync 2013 API exposes programmable types that let you create a telephone list administration interface in your application so that a user can create a list of telephone numbers where the user can be reached. Figure 1 shows a sample UI that lists the signed-in user’s telephone numbers. The text box, check box, and buttons on the right-hand side of the form let users change a telephone number, publish a number to their contact card, remove a number from their contact card, or remove a number from the list.

The following WPF form shows a list of user phone numbers on the upper left, a text box, a **publish** check box, a **Save Edit** button, a **Remove** button, and a presence indicator with a user’s full name.

Figure 1. Sample WPF form

  
![Screen shot of a phone manager sample](images/JJ933103.LyncClientSDK_UserPhoneNumberManagement(Office.15).jpg "Screen shot of a phone manager sample")

Phone number administration is available through the [Microsoft.Lync.Model.Self](https://msdn.microsoft.com/en-us/library/jj277683\(v=office.15\)) class. The **Self** class encapsulates the user who is currently signed in to Lync 2013. **Self** exposes the properties, methods, and events that are used to fill the telephone list on the sample, keep the list up to date when a user changes a telephone number with the Lync 2013 client, and start telephone list update operations. Other publishable contact card information such as personal notes, availability, display photo URLs, and location names are also published by calling methods on the **Self** class.

For information about how to create a telephone administration UI, see [How to: Update and publish user telephone numbers in Lync SDK](how-to-update-and-publish-user-telephone-numbers-in-lync-sdk.md).

### Contact card telephone numbers

The signed-in user is represented by the **Self** class and is represented by a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object obtained from the [Self.Contact](https://msdn.microsoft.com/en-us/library/jj275949\(v=office.15\)) property. This **Contact** object exposes a collection of telephone numbers for the local user and an event that is raised when the collection changes. The telephone number list that you get from the **Self** class might not be identical to the telephone number list you get from the **Contact** class for the same user. This is because the telephone number collection on the **Self** class includes telephone numbers that are not published on the user’s contact card. The telephone number list from the **Contact** object includes only numbers that are published on the contact card. If a user has entered a telephone number for each of the four telephone number types, but has published none of the numbers to the contact card, the **Contact** telephone number collection is empty while the **Self** telephone number collection has four telephone numbers.

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
<td><p>The contact card telephone number list is a list of all endpoints that a user can be reached on. This list includes the <a href="https://msdn.microsoft.com/en-us/library/jj275544(v=office.15)">ContactEndpointType</a><strong>.Lync</strong> and <a href="https://msdn.microsoft.com/en-us/library/jj275544(v=office.15)">ContactEndpointType</a><strong>.VoiceMail</strong>. These two types cannot be published or edited. For this reason, the types are not available from the <strong>Self</strong> class.</p></td>
</tr>
</tbody>
</table>

The **Contact** object telephone list is used to populate a contact card in your application UI. You cannot update a user’s telephone numbers by using the **Contact** object. You must use the **Self** object to update or publish telephone numbers to the user’s contact card.

## Additional resources

  - [Beyond the basics in Lync 2013 SDK](beyond-the-basics-in-lync-2013-sdk.md)

  - [How to: Update and publish user telephone numbers in Lync SDK](how-to-update-and-publish-user-telephone-numbers-in-lync-sdk.md)

