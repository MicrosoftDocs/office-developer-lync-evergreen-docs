---
title: Refreshing active subscriptions
TOCTitle: Refreshing active subscriptions
ms:assetid: 2e65a133-7865-49b3-ae73-5060daaa5c42
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454629(v=office.15)
ms:contentKeyID: 57092873
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Refreshing active subscriptions


**Applies to:** Lync 2013 | Lync Server 2013

In Microsoft Unified Communications Managed API 4.0, the process for refreshing remote presence subscriptions is performed by using an LocalEndpointPresenceServices object that can be obtained from an established (or connected) LocalEndpoint object.

Refreshing remote presence subscription is an asynchronous process. It applies to all the current subscriptions that are represented by the active RemotePresenceView objects. To refresh remote presence subscriptions, call BeginRefreshRemotePresenceViews/EndRefreshRemotePresenceViews methods. If the request is successful, the current values of the subscribed category instances, as specified in each active subscription view, will be returned as the PresenceNotificationReceived events and are handled by the same event handlers of the respective subscription.

The following code example shows how to refresh all active remote subscriptions.

```csharp
        #region Refresh all remote presence views
        public void RefreshRemoteSubscription()
        {
            _remotePresenceServices.BeginRefreshRemotePresenceViews(CallbackOnBeginRefreshReturned, _remotePresenceServices);
        }

        private void CallbackOnBeginRefreshReturned(IAsyncResult result)
        {
            try
            {
                LocalEndpointPresenceServices localEndpointPresenceServices = result.AsyncState as LocalEndpointPresenceServices;
                if (localEndpointPresenceServices == _remotePresenceServices)
                {
                    _remotePresenceServices.EndRefreshRemotePresenceViews(result);
                    if (OnRefreshPresenceViewsCompleted != null)
                        RaiseEvent(OnRefreshPresenceViewsCompleted, this,
                            new AsyncOpStatusEventArgs(AsyncOpStatus.OK, null));
                }
            }
            catch (Exception ex)
            {
                if (OnRefreshPresenceViewsCompleted != null)
                    RaiseEvent(OnRefreshPresenceViewsCompleted, this, 
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ex));
            }
        }
        #endregion Refresh all remote presence views
```

In this example, the results are returned in both PersistentPresenceReceivedEventHandler and PollingPresenceReceivedEventHandler. For an implementation of these event handlers, see [Handling events to receive presence publications](handling-events-to-receive-presence-publications.md).

## See also

#### Concepts

[Receiving Enhanced Presence](receiving-enhanced-presence.md)

