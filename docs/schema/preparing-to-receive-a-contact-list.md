---
title: Preparing to receive a contact list
TOCTitle: Preparing to receive a contact list
ms:assetid: 24f86fd2-4ceb-489a-8e90-5586be07c3a0
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454631(v=office.15)
ms:contentKeyID: 57092874
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Preparing to receive a contact list


**Applies to:** Lync 2013 | Lync Server 2013

In Microsoft Unified Communications Managed API 4.0, a contact list is stored, maintained, and retrieved by using a **ContactGroupServices** object. Obtaining this object from a signed-in endpoint is the first step in setting up and maintaining a contact list.

Retrieving a contact list is an asynchronous process. Contacts and groups are returned through event notifications. Properly configuring the event handling is a prerequisite to receiving the contact list.

In a typical application scenario, a contact list should display contact information, presence status, and other relevant data about each contact. In a Microsoft Lync Server 2013 deployment, this kind of information about a contact is obtained by using a separate subscription to the appropriate presence category instances that are published by the contact. Hence, the preparation involves setting up this remote presence subscription.

The following code example shows how these tasks are performed before receiving a contact list and the accompanying presence publications. It's an excerpt of a C\# class used throughout this section to show how to maintain a contact list in a UCMA application.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Forms;

using Microsoft.Rtc.Collaboration;
using Microsoft.Rtc.Collaboration.ContactsGroups;
using Microsoft.Rtc.Collaboration.Presence;
using UcmaAppLibrary;
using UcmaAppPresenceWatcher;

namespace UcmaAppContactManager
{
    /// <summary>
    /// Application object to encapsulate contact management for unified communications
    /// </summary>
    public class UcmaContactManager : UcmaObject
    {
        ContactGroupServices _cgServices;
        UserEndpointPresenceServices _cgPresenceServices; 
        RemotePresenceView _cgPresenceView;

        #region events for the subscription to receive contacts and groups
        public event EventHandler<PresenceSubscriptionStateChangedEventArgs> OnContactGroupSubscriptionStateChanged;
        public event EventHandler<ContactGroupNotificationEventArgs> OnContactGroupNotificationReceived;
        #endregion events for the subscription to receive contacts and groups

        #region events for the subscription to receive the contacts' presence
        public event EventHandler<RemotePresentitiesNotificationEventArgs> OnContactPresenceReceived;
        public event EventHandler<RemoteSubscriptionStateChangedEventArgs> OnContactPresenceSubscriptionStateChanged;
        #endregion events for the subscription to receive contacts' presence

        #region Prepare to receive contacts/groups and their presence publications.
        /// <summary>
        /// Class constructor that creates and initializes two subscriptions:
        ///    1. The subscription to contacts and groups, managed using ContactGroupServices
        ///    2. The subscription to presence of the contacts, managed using RemotePresenceView
        ///       and UserEndpointPresenceServices 
        /// </summary>
        /// <param name="endpoint"></param>
        public UcmaContactManager(UserEndpoint endpoint)
        {
            // Prepare to receive and manage contacts and groups
            _cgServices = endpoint.ContactGroupServices;
            _cgServices.NotificationReceived +=
                new EventHandler<ContactGroupNotificationEventArgs>(
                    ContactsNotificationReceivedEventHandler);
            _cgServices.SubscriptionStateChange += 
                new EventHandler<PresenceSubscriptionStateChangedEventArgs>(
                    ContactsSubscriptionStateChangedEventHandler);


            // Prepare to receive the presence publication by the contacts 
            _cgPresenceServices = endpoint.PresenceServices;
            RemotePresenceViewSettings rpvs = new RemotePresenceViewSettings();
            _cgPresenceView = new RemotePresenceView(endpoint, rpvs);
            _cgPresenceView.PresenceNotificationReceived +=
                new EventHandler<RemotePresentitiesNotificationEventArgs>(
                    ContactPresenceNotificationReceivedEventHandler);
            _cgPresenceView.SubscriptionStateChanged +=
                new EventHandler<RemoteSubscriptionStateChangedEventArgs>(
                    ContactPresenceSubscriptionStateChangedEventHandler);
           
        }
        #endregion Prepare to receive contacts (and groups) and their presence publications.

        #region Event handlers to receive contacts and groups
        void ContactsNotificationReceivedEventHandler(object sender, ContactGroupNotificationEventArgs e)
        {
            if (OnContactGroupNotificationReceived != null)
                RaiseEvent(OnContactGroupNotificationReceived, sender, e);

            // Start to receive the presence publications by the immediate received contacts
            this.SubscribeToContactsPresence(e.Contacts);
        }

        void ContactsSubscriptionStateChangedEventHandler(object sender, PresenceSubscriptionStateChangedEventArgs e)
        {
            if (OnContactGroupSubscriptionStateChanged != null)
                RaiseEvent(OnContactGroupSubscriptionStateChanged, sender, e);
        }
        #endregion Event handlers to receive contacts and groups

        #region Event handlers to receive contacts' presence publications
        /// <summary>
        /// Event handler to receive subscription state changes as events raised by 
        /// the RemotePresenceView object for the presence subscription:
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ContactPresenceSubscriptionStateChangedEventHandler(object sender, RemoteSubscriptionStateChangedEventArgs e)
        {            
            if (OnContactPresenceSubscriptionStateChanged != null)
                RaiseEvent(OnContactPresenceSubscriptionStateChanged, sender, e);
        }

        /// <summary>
        /// Event handler to receive contact’s presence as events raised by
        /// the RemotePresenceView object for the presence subscription:
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ContactPresenceNotificationReceivedEventHandler(object sender, RemotePresentitiesNotificationEventArgs e)
        {
            if (OnContactPresenceReceived != null)
                RaiseEvent(OnContactPresenceReceived, sender, e);               
        }

        #endregion Event handlers to receive contacts' presence publications



    }
}
```

In this example, the contact list is managed by a ContactGroupServices object (\_cgServices) whereas the subscription to the presence publications by the contacts in the list is managed by a RemotePresenceView object (\_cgPresenceView) and a UserEndpointPresenceServices object (\_cgPresenceServices). Entries of the contact list, in the form of contacts and groups category instances, are returned in the NotificationReceived events that are raised by the \_cgServices, as soon as a SUBSCRIBE request is successfully submitted through the ContactGroupServices object. The events are handled by using the ContactsNotificationReceivedEventhandler routine. In this example, the handling of this kind of event includes propagating the received contact list entries to the caller and starting the presence subscription (this.SubscribeToContactsPresence(e.Contacts)) by the just received contacts. In turn, the presence publications are returned in the ContactPresenceNotificationReceivedEventHandler routine, which sends the results to the caller interested in receiving and displaying the results.

## See also

#### Concepts

[Managing self-published contact lists](managing-self-published-contact-lists.md)

