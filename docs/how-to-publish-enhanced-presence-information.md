---
title: 'How to: Publish enhanced presence information'
TOCTitle: 'How to: Publish enhanced presence information'
ms:assetid: 2bc5760d-1b39-47fd-8f67-adf21bb83a16
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937288(v=office.15)
ms:contentKeyID: 50877108
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Publish enhanced presence information

Learn how to publish Microsoft Lync 2013 presence information such as the availability and personal note of a Lync 2013 contact by using methods in Microsoft Lync 2013 SDK.

**Last modified:** July 01, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Publish enhanced presence information<br />
Code examples: Publish presence information<br />
Next steps<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-use-the-lync-47ded7b4">Use the Lync 2013 Model API to retrieve and publish presence</a><br />
</p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for publishing enhanced presence information are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

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
<td><p><a href="enhanced-presence-content-in-lync-sdk.md">Enhanced presence content in Lync SDK</a></p></td>
<td><p>Describes how Microsoft Lync 2013 enhances the industry standard SIP simple presence.</p></td>
</tr>
<tr class="even">
<td><p><a href="presence-publication-and-subscription-in-lync-sdk.md">Presence publication and subscription in Lync SDK</a></p></td>
<td><p>Describes what it means to publish and subscribe to enhanced presence in Lync 2013.</p></td>
</tr>
</tbody>
</table>

This process involves defining an array of contact information types and a Dictionary\<[PublishableContactInformationType](https://msdn.microsoft.com/en-us/library/jj293821\(v=office.15\)), object\> that holds the contact information to be published. Publishing a set of contact information items raises the [ContactInformationChanged](https://msdn.microsoft.com/en-us/library/jj275543\(v=office.15\)) event on the publishing contact. If the publishing contact is the local user, the event is raised both locally and for remote users who have subscribed to the local contact.

## Publish enhanced presence information

The following illustration shows the classes, methods, and events used in the process of publishing contact information.

![OCOM\_Self\_Publish](images/JJ937288.OCOM_Self_Publish(Office.15).jpg "OCOM_Self_Publish")

### To publish enhanced presence information

1.  Get the [LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance and verify that the client is signed in to the server.
    
    For information about signing in to Microsoft Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

2.  Create a Dictionary\<[PublishableContactInformationType](https://msdn.microsoft.com/en-us/library/jj293821\(v=office.15\)), object\> of contact information types and the corresponding values to be updated.
    
    The Dictionary you declare and instantiate is passed into [BeginPublishContactInformation](https://msdn.microsoft.com/en-us/library/jj278107\(v=office.15\)).

3.  Add a [ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\)) and the corresponding publishable value to the dictionary you created previously.

4.  Read the [Self](https://msdn.microsoft.com/en-us/library/jj277589\(v=office.15\)) property to get an instance of [Self](https://msdn.microsoft.com/en-us/library/jj277683\(v=office.15\)).

5.  Optional: Declare and instantiate a state object such as a string and fill it with appropriate state information.
    
    The callback method you provide should access this state information to provide a context for the operation.

6.  Call [BeginPublishContactInformation](https://msdn.microsoft.com/en-us/library/jj278107\(v=office.15\)), passing the dictionary, the callback method (or null), and the state object.

## Code examples: Publish presence information

The following examples publish the presence information typically published in a custom application.

### Publish a personal note and current availability

The following example method publishes a new personal note for the local user.

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
<td><p>In the example, a callback method is included as a parameter in the <strong>PublishPresenceItems</strong> method call. You should pass a null value in the callback parameter position if you are not interested in catching the result of the publication.</p></td>
</tr>
</tbody>
</table>

``` csharp
        /// <summary>
        /// Publishes an update to a personal note
        /// </summary>
        /// <param name="newNote">string. The new personal note text.</param>
        public void PublishPersonalNoteAndFreeAvailability(string newNote)
        {
            //Each element of this array must contain a valid enumeration. If null array elements 
            //are passed, an ArgumentException is raised.
            Dictionary<PublishableContactInformationType, object> publishData = new Dictionary<PublishableContactInformationType, object>();
            publishData.Add(PublishableContactInformationType.PersonalNote, newNote);
            publishData.Add(PublishableContactInformationType.Availability, ContactAvailability.Free);

            //Helper method is found in the next example.
            SendPublishRequest(publishData, "Personal Note and Availability");
        }
```

The following example begins the asynchronous publication process.

``` csharp
        /// <summary>
        /// Sends a publication request and handles any exceptions raised.
        /// </summary>
        /// <param name="publishData">Dictionary. Information to be published.</param>
        /// <param name="PublishId">string. Unique publication identifier.</param>
        private void SendPublishRequest(
           Dictionary<PublishableContactInformationType, object> publishData,
            string PublishId)
        {

            try
            {
                _LyncClient.Self.BeginPublishContactInformation(
                    publishData,
                    (ar) => {
                        _LyncClient.Self.EndPublishContactInformation(ar);
                    },
                    null);
            }
            catch (COMException ce)
            {
                MessageBox.Show("publish COM exception: " + ce.ErrorCode.ToString());
            }
            catch (ArgumentException ae)
            {
                MessageBox.Show("publish Argument exception: " + ae.Message);
            }
        }
```

The following example handles the [ContactInformationChanged](https://msdn.microsoft.com/en-us/library/jj275543\(v=office.15\)) event that is raised when the current contact information state changes. The example uses a message box to notify a user that presence has been updated and then removes the registration for [Contact](https://msdn.microsoft.com/en-us/library/jj275949\(v=office.15\)) information update events.

``` csharp
        /// <summary>
        /// Handles event raised when the presence of a contact has been updated
        /// </summary>
        /// <param name="source">Contact. Contact instance whose presence is updated</param>
        /// <param name="data">PresenceItemsChangedEventArgs. Collection of presence item types whose values have been updated.</param>
        void Contact_ContactInformationChanged(object sender, ContactInformationChangedEventArgs e)
        {
            if (((Contact)source) == _LyncClient.Self.Contact)
            {
                System.Text.StringBuilder sb = new System.Text.StringBuilder();
                sb.Append("Changed types: " + System.Environment.NewLine);
                foreach (ContactInformationType changedInformationType in e.ChangedContactInformation)
                {
                    sb.Append(changedInformationType.ToString() + System.Environment.NewLine);
                }
                MessageBox.Show("Self publish succeeded: " + sb.ToString());
            }
        }
```

### Reset availability to default contact availability

To reset a user’s current availability to the default availability calculated by the Lync 2013 client, publish [ContactAvailability](https://msdn.microsoft.com/en-us/library/jj293978\(v=office.15\))**.None**.

``` csharp
        /// <summary>
        /// Publishes default client availability
        /// </summary>

        public void PublishDefaultAvailability()
        {
            //Each element of this array must contain a valid enumeration. If null array elements 
            //are passed, an ArgumentException is raised.
            Dictionary<PublishableContactInformationType, object> publishData = new Dictionary<PublishableContactInformationType, object>();
            publishData.Add(PublishableContactInformationType.Availability, ContactAvailability.None);

            //Helper method is found in the next example.
            SendPublishRequest(publishData, "Reset availability to default");
        }
```

## Next steps

  - [How to: Subscribe to enhanced presence content](how-to-subscribe-to-enhanced-presence-content.md)

  - [How to: Use presence information in an application](how-to-use-presence-information-in-an-application.md)

## Additional resources

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

