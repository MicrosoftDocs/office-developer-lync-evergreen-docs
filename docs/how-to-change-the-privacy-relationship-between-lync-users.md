---
title: 'How to: Change the privacy relationship between Lync users'
TOCTitle: 'How to: Change the privacy relationship between Lync users'
ms:assetid: f2e80755-67a6-4ccc-91dd-7c5e4146fd95
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933227(v=office.15)
ms:contentKeyID: 50877371
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Change the privacy relationship between Lync users

Learn about how to programmatically change the privacy relationship between two Microsoft Lync 2013 contacts by using Microsoft Lync 2013 SDK.

**Last modified:** July 01, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Privacy relationship options<br />
Change the privacy relationship of a contact<br />
Code example: Accepting parameters<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for using presence information in an application are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Privacy relationship options

The following table presents the publishable contact information types that are available to contacts assigned to the five privacy access levels.

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Types/relationship</p></th>
<th><p>Friend</p></th>
<th><p>Workgroup</p></th>
<th><p>Colleague</p></th>
<th><p>External</p></th>
<th><p>Blocked</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Phones</strong></p></td>
<td><p>Mobile, home, and any other published phone numbers.</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>None.</p></td>
</tr>
<tr class="even">
<td><p><strong>Contact information</strong></p></td>
<td><p>Display name, email address, job title, display photo, company, office location, and work phone number.</p></td>
<td><p>Display name, email address, job title, company, and display photo.</p></td>
<td><p>Display name, email address, company, job title, and display photo.</p></td>
<td><p>Display name, email address, company, job title, and display photo.</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Voicemail</strong></p></td>
<td><p>Voicemail URL when the user is enabled for Lync.</p></td>
<td><p>Voicemail URL when the user is enabled for Lync.</p></td>
<td><p>Voicemail URL when the user is enabled for Lync.</p></td>
<td><p>Voicemail URL when the user is enabled for Lync.</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Working calendar</strong></p></td>
<td><p>The working-hour blocks as specified in the user’s calendar.</p></td>
<td><p>The working-hour blocks as specified in the user’s calendar.</p></td>
<td><p>The working-hour blocks as specified in the user’s calendar.</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Free/busy calendar</strong></p></td>
<td><p>The time periods when the user is free or busy according to the user’s calendar.</p></td>
<td><p>The time periods when the user is free or busy according to the user’s calendar.</p></td>
<td><p>The time periods when the user is free or busy according to the user’s calendar.</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Notes</strong></p></td>
<td><p>Presence note or OOF message from the user's Outlook account.</p></td>
<td><p>Presence note or OOF message from the user's Outlook account.</p></td>
<td><p>Presence note or OOF message from the user's Outlook account.</p></td>
<td><p>Presence note or OOF message from the user's Outlook account.</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Change the privacy relationship of a contact

### To change the privacy relationship of a contact

1.  Get the [LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance and verify that the client state is signed in to the server.
    
    For information, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

2.  Get the [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) instance to be updated.
    
    Any valid contact, regardless of its source, can be updated to change the privacy relationship setting. For information about getting the contacts in a user’s contact list, see [How to: Display a contact list](how-to-display-a-contact-list.md).

3.  Call the [Contact.BeginChangeSetting](https://msdn.microsoft.com/en-us/library/jj275533\(v=office.15\)) method, specifying that the privacy relationship is to be set by setting the [ContactSetting](https://msdn.microsoft.com/en-us/library/jj267670\(v=office.15\)).**AccessLevel** and by an [AccessLevel](https://msdn.microsoft.com/en-us/library/jj266987\(v=office.15\)) enumerator representing the new privacy relationship.

4.  Catch the **System.IAsyncResult** returned from the call.

5.  Call [Contact.EndChangeSetting](https://msdn.microsoft.com/en-us/library/jj266039\(v=office.15\)) to complete the operation.
    
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/JJ933112.alert_note(Office.15).gif" title="Tip" alt="Tip" /><strong>Tip</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>If you do not want to block execution on your UI thread while the operation runs, pass a <strong>System.AsyncCallback</strong> method into <strong>BeginChangeSetting</strong> and make the <a href="https://msdn.microsoft.com/en-us/library/jj266039(v=office.15)">EndChangeSetting</a> call inside the callback.</p></td>
    </tr>
    </tbody>
    </table>

## Code example: Accepting parameters

The following example accepts two string parameters representing the URI of a user and the new access level desired. The access level string is converted to an [AccessLevel](https://msdn.microsoft.com/en-us/library/jj266987\(v=office.15\)) enumerator before an instance of [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) is obtained from [ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)) by calling into [GetContactByUri](https://msdn.microsoft.com/en-us/library/jj274481\(v=office.15\)).

The contact setting, [ContactSetting](https://msdn.microsoft.com/en-us/library/jj267670\(v=office.15\)).**AccessLevel**, is set by calling into [Contact.BeginChangeSetting](https://msdn.microsoft.com/en-us/library/jj275533\(v=office.15\)) and passing both an enumerator for the property to be updated and an enumerator for the new property value.

``` csharp
        /// <summary>
        /// Updates the privacy relationship of a contact specified by Uri
        /// </summary>
        /// <param name="ContactUri">string. Uri of contact to update.</param>
        /// <param name="newAccessLevel">string. New privacy relationship.</param>
        public void UpdatePrivacyRelationship(string ContactUri, string newAccessLevel)
        {
            AccessLevel newLevelEnumerator = AccessLevel.Default;
            switch (newAccessLevel.ToUpper().Trim())
            { 
                case "FRIENDS":
                    newLevelEnumerator = AccessLevel.Friends;
                    break;
                case "WORKGROUP":
                    newLevelEnumerator = AccessLevel.Workgroup;
                    break;
                case "COLLEAGUE":
                    newLevelEnumerator = AccessLevel.Colleague;
                    break;
                case "EXTERNAL":
                    newLevelEnumerator = AccessLevel.External;
                    break;
                case "BLOCKED":
                    newLevelEnumerator = AccessLevel.Blocked;
                    break;
            }
            Contact contactToUpdate = _LyncClient.ContactManager.GetContactByUri(ContactUri);
            if (contactToUpdate != null)
            {
                contactToUpdate.BeginChangeSetting(ContactSetting.AccessLevel, newLevelEnumerator, SetPrivacyCallback, contactToUpdate);
            }
        }

        /// <summary>
        /// Handles async callback when set privacy operation completes
        /// </summary>
        /// <param name="ar">IAsyncResult. The state of the operation.</param>
        private void SetPrivacyCallback(IAsyncResult ar)
        {
            if (ar.IsCompleted == true)
            {
                ((Contact)ar.AsyncState).EndChangeSetting(ar);
                Console.WriteLine("Privacy relationship updated for " + ((Contact)ar.AsyncState).GetContactInformation(ContactInformationType.DisplayName).ToString());
            }
        }
```

## Additional resources

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

