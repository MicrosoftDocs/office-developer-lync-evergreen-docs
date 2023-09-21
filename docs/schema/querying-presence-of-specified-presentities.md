---
title: Querying presence of specified presentities
TOCTitle: Querying presence of specified presentities
ms:assetid: 1cd62781-d9c3-4b99-a967-fe500cf7d954
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454623(v=office.15)
ms:contentKeyID: 57092869
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Querying presence of specified presentities


**Applies to:** Lync 2013 | Lync Server 2013

In Microsoft Unified Communications Managed API 4.0, the process used to query presence is performed with an LocalEndpointPresenceServices object that can be obtained from an established (or connected) LocalEndpoint object.

Querying presence is an asynchronous process. Each query corresponds to a single SUBSCRIBE request that is submitted by or on behalf of the user. A client starts a query by using the BeginPresenceQuery/EndPresenceQuery pattern supported by the LocalEndpointPresenceServices object. The query results are returned by invoking the event handler that is passed in to the call to BeginPresenceQuery as the queryResultHandler parameter.

The following code example shows how to query specified categories that are published by the specified presentities.

```csharp
        #region Querying remote presence
        public void QueryRemotePresence(string[] targets, string[] categories)
        {
            QueryRemotePresence(targets, categories, QueryingPresenceReceivedEventHandler);
        }

        public void QueryRemotePresence(string[] presentityUris, string[] categoryNames, 
            EventHandler<RemotePresentitiesNotificationEventArgs> queryResultHandler)
        {
            _remotePresenceServices.BeginPresenceQuery(
                presentityUris, 
                categoryNames, 
                queryResultHandler,
                CallbackOnBeginPresenceQueryReturned, 
                _remotePresenceServices);
        }

        private void CallbackOnBeginPresenceQueryReturned(IAsyncResult result)
        {
            try
            {
                if (_remotePresenceServices == result.AsyncState as LocalEndpointPresenceServices)
                {
                    _remotePresenceServices.EndPresenceQuery(result);
                    // inform the caller of the OK status of the PresenceQuery operation.
                    if (OnQueryPresenceCompleted != null)
                        RaiseEvent(OnQueryPresenceCompleted, this,
                            new AsyncOpStatusEventArgs(AsyncOpStatus.OK, null));
                }
            }
            catch (Exception ex)
            {
                // inform the caller of the Error status of the presence querying operation.
                if (OnQueryPresenceCompleted != null)
                    RaiseEvent(OnQueryPresenceCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ex));
            }
        }
        #endregion Querying remote presence
```

In this example, the query results are returned in the QueryingPresenceReceivedEventHandler handler. Its implementation appears in [Preparing to receive presence publications](preparing-to-receive-presence-publications.md).

## See also

#### Concepts

[Receiving Enhanced Presence](receiving-enhanced-presence.md)

