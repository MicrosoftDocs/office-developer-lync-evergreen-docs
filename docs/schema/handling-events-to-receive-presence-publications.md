---
title: Handling events to receive presence publications
TOCTitle: Handling events to receive presence publications
ms:assetid: a4484575-6a10-4952-bef0-fd86ca53d1f7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454654(v=office.15)
ms:contentKeyID: 57092907
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Handling events to receive presence publications


_**Applies to:** Lync 2013 | Lync Server 2013_

The following code example shows how to receive remote presence in the event handlers for persistent and polling subscriptions as well as for queries.

``` csharp
        #region Event handlers for persistent subscription 
        void PersistentPresenceReceivedEventHandler(object sender,
            RemotePresentitiesNotificationEventArgs e)
        {
            if (OnPersistentPresenceReceived != null)
                RaiseEvent(OnPersistentPresenceReceived, this, e);
        }

        void PersistentSubscriptionStateChangedEventHandler(object sender,
            RemoteSubscriptionStateChangedEventArgs e)
        {
            if (OnPersistentSubscriptionStateChanged != null)
                RaiseEvent(OnPersistentSubscriptionStateChanged, this, e);
        }
        #endregion Event handlers for persistent subscription

        #region Event handlers for polling subscription
        void PollingPresenceReceivedEventHandler(object sender,
            RemotePresentitiesNotificationEventArgs e)
        {
            if (OnPollingPresenceReceived != null)
                RaiseEvent(OnPollingPresenceReceived, this, e);
        }

        void PollingSubscriptionStateChangedEventHandler(object sender,
            RemoteSubscriptionStateChangedEventArgs e)
        {
            if (OnPollingSubscriptionStateChanged != null)
                RaiseEvent(OnPollingSubscriptionStateChanged, this, e);
        }

        #endregion Event handlers for polling subscription

        #region Event handlers for querying subscription
        void QueryingPresenceReceivedEventHandler(object sender,
            RemotePresentitiesNotificationEventArgs e)
        {
            if (OnQueryingPresenceReceived != null)
                RaiseEvent(OnQueryingPresenceReceived, this, e);
        }

        #endregion Event handlers for querying subscription

```

In this example, the received presence data are passed through in an event argument as an instance of the RemotePresentitiesNotificationEventArgs type. The actual processing of the presence data is deferred to the caller of the UcmaPresenceWatcher class.

For the persistent and polling subscriptions, the subscription can be started if the subscription is not in a terminated state. The event notifications are dispatched when the subscription state is PresenceState.Subscribed. Thus, an application should handle subscription state changed events to ensure that invalid operations are not permitted and appropriate expectations are addressed.

## See also

#### Concepts

[Receiving Enhanced Presence](receiving-enhanced-presence.md)

