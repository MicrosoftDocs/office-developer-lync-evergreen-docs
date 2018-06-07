---
title: Preparing to receive presence publications
TOCTitle: Preparing to receive presence publications
ms:assetid: b35c72f3-8201-4274-b33b-299943143de6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454656(v=office.15)
ms:contentKeyID: 57092917
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Preparing to receive presence publications


**Applies to:** Lync 2013 | Lync Server 2013

Your application can receive presence publications by other users by using a persistent or polling subscription. It can also receive the publications by submitting a query with the specified category names and presentities. Before your application can receive any presence publications, the user must sign in to the underlying Microsoft Lync Server 2013 instance. For more information, see [Signing in to Lync Server](signing-in-to-lync-server.md).

In Microsoft Unified Communications Managed API 4.0, a subscription, either persistent or polling, is managed by using a RemotePresenceView object. A query is handled by using a LocalEndpointPresenceServices object. Together, they support the following operations:

  - Start and stop a persistent subscription.

  - Start and stop a polling subscription.

  - Refresh all active subscriptions.

  - Submit a query.

The operations are asynchronous and the client must also implement the required event handlers. To prepare and receive presence publications, complete the following tasks:

  - Obtain the RemotePresenceView and LocalEndpointPresenceServices objects.

  - Register for events to be raised by the RemotePresenceView and LocalEndpointPresenceServices objects.

  - Implement the required event handlers to receive event notifications.

For more information about event implementation, see [Handling events to receive presence publications](handling-events-to-receive-presence-publications.md).

The following code example shows how to prepare for remote presence subscriptions and queries. The example is an excerpt of the C\# **UcmaPresenceWatcher** class that is used to include the other programming aspects of presence subscription and query that appear in this section.

``` csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.Rtc.Collaboration;
using Microsoft.Rtc.Collaboration.Presence;
using Microsoft.Rtc.Collaboration.ContactsGroups;
using Microsoft.Rtc.Signaling;
using UcmaAppLibrary;

namespace PresenceWatcher 
{
    /// <summary>
    /// Encapsulates remote presence subscription and queries on a local endpoint. 
    /// A presence watcher can receive presence notifications by using:
    ///   1. Persistent subscription in real time
    ///   2. Polling subscription at prescribed fixed intervals of time
    ///   3. Querying remote presence on demand
    ///   4. Refreshing remote presence views
    ///   
    /// The subscriptions are managed by using instances of the RemotePresenceView class.
    /// The query is handled using the LocalEndpointPresenceServices class.
    /// Subscription refresh are handled using LocalEndpointPresenceServices class.
    /// </summary>
    public class UcmaPresenceWatcher : UcmaObject
    {
        protected LocalOwnerPresence _localPresenceServices;
        protected LocalEndpointPresenceServices _remotePresenceServices;
        protected RemotePresenceView _persistentPresenceView;
        protected RemotePresenceView _pollingPresenceView;

        #region process-related events
        public event EventHandler<AsyncOpStatusEventArgs> OnQueryPresenceCompleted;
        public event EventHandler<AsyncOpStatusEventArgs> OnSubscribeToPresenceCompleted;
        public event EventHandler<AsyncOpStatusEventArgs> OnRefreshPresenceViewsCompleted;
        #endregion process-related events

        #region results-related events
        public event EventHandler<RemotePresentitiesNotificationEventArgs> OnPersistentPresenceReceived;
        public event EventHandler<RemoteSubscriptionStateChangedEventArgs> OnPersistentSubscriptionStateChanged;

        public event EventHandler<RemotePresentitiesNotificationEventArgs> OnPollingPresenceReceived;
        public event EventHandler<RemoteSubscriptionStateChangedEventArgs> OnPollingSubscriptionStateChanged;

        public event EventHandler<RemotePresentitiesNotificationEventArgs> OnQueryingPresenceReceived;
        #endregion results-related events

        #region class constructor
        /// <summary>
        /// Constructor of a presence watcher supporting persistent, polling and on-demand subscriptions 
        /// to presence categories published by specified remote presentities. On-demand subscription is 
        /// also known as presence query. The code here also handles self-presence.
        /// </summary>
        /// <param name="endpoint"></param>
        public UcmaPresenceWatcher(LocalEndpoint endpoint)
        {
            _remotePresenceServices = endpoint.PresenceServices;

            // RemotePresenceView for persitent subscription:
            RemotePresenceViewSettings rpvs = new RemotePresenceViewSettings();
            rpvs.SubscriptionMode = RemotePresenceViewSubscriptionMode.Persistent;
            
            _persistentPresenceView = new RemotePresenceView(endpoint, rpvs);
            _persistentPresenceView.PresenceNotificationReceived += 
                new EventHandler<RemotePresentitiesNotificationEventArgs>(
                    PersistentPresenceReceivedEventHandler);
            _persistentPresenceView.SubscriptionStateChanged += 
                new EventHandler<RemoteSubscriptionStateChangedEventArgs>(
                    PersistentSubscriptionStateChangedEventHandler);
            
            // RemotePresenceView for polling subscription
            rpvs = new RemotePresenceViewSettings();
            rpvs.SubscriptionMode = RemotePresenceViewSubscriptionMode.Polling;
            rpvs.PollingInterval = new TimeSpan(0, 5, 0);  // every 5 minutes
            _pollingPresenceView = new RemotePresenceView(endpoint, rpvs);
            _pollingPresenceView.SetPresenceSubscriptionCategoriesForPolling(
                new string[] { "contactCard", "state", "note", "noteHistory" });
            _pollingPresenceView.PresenceNotificationReceived += 
                new EventHandler<RemotePresentitiesNotificationEventArgs>(
                    PollingPresenceReceivedEventHandler);
            _pollingPresenceView.SubscriptionStateChanged += 
                new EventHandler<RemoteSubscriptionStateChangedEventArgs>(
                    PollingSubscriptionStateChangedEventHandler);

        }
        #endregion class constructor
    }
}

```

## See also

#### Concepts

[Receiving Enhanced Presence](receiving-enhanced-presence.md)

