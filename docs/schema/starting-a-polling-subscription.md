---
title: Starting a Polling Subscription
TOCTitle: Starting a Polling Subscription
ms:assetid: b0d6c4dd-9eda-4a38-a9b0-c0c76818a596
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454657(v=office.15)
ms:contentKeyID: 57092919
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Starting a Polling Subscription


**Applies to:** Lync 2013 | Lync Server 2013

After the RemotePresenceView object for a polling subscription is created and initialized, you can start the polling subscription by calling the StartSubscribingToPresentities method on the RemotePresenceView object of the Polling type.

As in a persistent subscription, Microsoft Unified Communications Managed API 4.0 assigns calendarData, contactCard, note, noteHistory, state, and services as the default subscription category names in a polling subscription. You can reset them by calling the RemotePresenceView.SetPresenceSubscriptionCategoriesForPolling method before starting the subscription. The polling interval has a default value of 5 minutes and you can reset this value by calling the RemotePresenceViewSettings.SetPresenceSubscriptionCategoriesPollingInterval instance when the RemotePresenceView of the Polling type is instantiated.

Polling subscription is an asynchronous process and involves multiple SUBSCRIBE requests, each being submitted on behalf of the user at the prescribed time intervals, until the subscription is terminated. With each successful SUBSCRIBE request, the server returns the requested results in PresenceNotificationReceived events. The client does not receive any presence notifications until the subscription state changes to Polling and unless the client has registered the required event handlers with the RemotePresenceView object. For information about registering for persistent subscription events, see [Handling events to receive presence publications](handling-events-to-receive-presence-publications.md).

To stop the subscription, call the StartUnsubscribingToPresentities method on the RemotePresenceView object. The terminated presence view object can be used to restart the subscription.

The following code example shows how to start and stop a polling subscription.

``` csharp
        #region Polling subscription
        public void SetPollingCategories(params string[] categoryNames)
        {
            if (categoryNames == null || categoryNames.Length == 0)
                return;
            _pollingPresenceView.SetPresenceSubscriptionCategoriesForPolling(categoryNames);
        }

        public void StartPollingSubscription(params string[] sipUris)
        {
            IEnumerable<string> uris = sipUris as IEnumerable<string>;
            this.StartPollingSubscription(uris);
        }

        public void StartPollingSubscription(IEnumerable<string> sipUris)
        {
            List<RemotePresentitySubscriptionTarget> sipUriList = new List<RemotePresentitySubscriptionTarget>();
            foreach (string sipUri in sipUris)
                sipUriList.Add(new RemotePresentitySubscriptionTarget(sipUri));
            _pollingPresenceView.StartSubscribingToPresentities(sipUriList.ToArray());
        }

        public void StopPollingSubscription(IEnumerable<string> sipUris)
        {
            _pollingPresenceView.StartUnsubscribingToPresentities(sipUris);
        }

        public void StopPollingSubscription()
        {
            IEnumerable<string> sipUris = _pollingPresenceView.GetPresentities();
            if (sipUris != null)
                this.StopPollingSubscription(sipUris);
        }

        #endregion polling subscription
```

## See also

#### Concepts

[Receiving Enhanced Presence](receiving-enhanced-presence.md)

