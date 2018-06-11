---
title: Starting a persistent subscription
TOCTitle: Starting a persistent subscription
ms:assetid: ba2a589b-e7d9-4565-a251-eb313c9af4bc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454655(v=office.15)
ms:contentKeyID: 57092910
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Starting a persistent subscription


**Applies to:** Lync 2013 | Lync Server 2013

After the RemotePresenceView object for a persistent subscription is created and initialized, you can start the persistent subscription by calling the StartSubscribingToPresentities method on the RemotePresenceView instance of the Persistent type.

By default, Microsoft Unified Communications Managed API 4.0 includes calendarData, contactCard, note, noteHistory, state, and services as the subscription category names in a persistent subscription. The subscription category names can be modified only before any SUBSCRIBE request is made. You can change this list by setting the UserEndpointSettings.Presence.RemotePresenceSubscriptionCategories property when UserEndpoint is instantiated. For an example that shows how to modify this list of subscription categories, see the code example in [Signing in to Lync Server](signing-in-to-lync-server.md).

Persistent subscription is an asynchronous process and involves a single SUBSCRIBE request that is submitted on behalf of the user. After the client successfully starts the subscription, the server returns the requested results in PresenceNotificationReceived events. When a new publication is detected or an existing publication is modified, the server returns the new results in more events. This process continues until the subscription is terminated.

To stop the subscription, call the StartUnsubscribingToPresentities method on the RemotePresenceView object. The terminated presence view object can be used to restart the subscription.

The following code example shows how to start and stop a persistent subscription.

```csharp
        #region Persistent subscription

        public void StartPersistentSubscription(IEnumerable<string> uris)
        {
            if (uris == null)
                return;
            List<RemotePresentitySubscriptionTarget> targets = new List<RemotePresentitySubscriptionTarget>();
            foreach (string uri in uris)
                targets.Add(new RemotePresentitySubscriptionTarget(uri));
            _persistentPresenceView.StartSubscribingToPresentities(targets);
        }

        public void StopPersistentSubscription(IEnumerable<string> uris)
        {
            if (uris == null)
                return;
            _persistentPresenceView.StartUnsubscribingToPresentities(uris);
        }


        public void StopPersistentSubscription()
        {
            this.StopPersistentSubscription(_persistentPresenceView.GetPresentities());
        }


        #endregion Persistent subscription
```

The client does not receive any presence notifications until the subscription state changes to Subscribed and the client registers the required event handlers with the RemotePresenceView object. For information about registering for persistent subscription events, see [Handling events to receive presence publications](handling-events-to-receive-presence-publications.md).

## See also

#### Concepts

[Receiving Enhanced Presence](receiving-enhanced-presence.md)

