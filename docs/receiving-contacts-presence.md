---
title: Receiving contacts presence
TOCTitle: Receiving contacts presence
ms:assetid: 757aef59-3d0a-4b59-974f-2fb41d890915
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454647(v=office.15)
ms:contentKeyID: 57093010
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Receiving contacts presence


_**Applies to:** Lync 2013 | Lync Server 2013_

The subscription to contacts and groups category instances provides a mechanism to maintain the identities of a user’s contacts and groups across different application sessions and to roam the list across multiple established endpoints. However, the contact list constructed in this manner does not specify any presence information about the contained contacts. In many application scenarios, a contact list requires that presence and other information about a contact be displayed as well. In any Microsoft Lync Server 2013 deployment, the contact’s presence information is obtained through a separate remote subscription to presence categories by the contacts in the contact list. For more information about receiving the presence of each contact after the contact list is obtained, see [Receiving Enhanced Presence](receiving-enhanced-presence.md).

The following code example shows how to manage the subscription to contacts presence. It shows the programming tasks that are used to subscribe and unsubscribe to the contacts presence, to refresh an ongoing subscription to the contacts presence, and to make on-demand queries of the contacts presence. For more information about initializing a contacts presence subscription, see [Preparing to receive a contact list](preparing-to-receive-a-contact-list.md).

``` csharp
        #region Managing contacts' presence subscription

        /// <summary>
        /// Start to receive contacts presence publications. It is called when the specified 
        /// contacts are added to the contact list
        /// </summary>
        /// <param name="contacts"></param>
        public void SubscribeToContactsPresence(
            System.Collections.ObjectModel.Collection<NotificationItem<Contact>> contacts)
        {
            List<RemotePresentitySubscriptionTarget> targets =
                new List<RemotePresentitySubscriptionTarget>();
            foreach (NotificationItem<Contact> contactItem in contacts)
            {
                targets.Add(new RemotePresentitySubscriptionTarget(contactItem.Item.Uri));
            }
            _cgPresenceView.StartSubscribingToPresentities(targets);
        }

        /// <summary>
        /// Stop receiving contacts presence publications. It is called when the specified contacts
        /// are deleted from the contact list
        /// </summary>
        /// <param name="sipUris"></param>
        public void UnsubscribeToContactsPresence(string[] sipUris)
        {
            if (sipUris != null)
            {
                _cgPresenceView.StartUnsubscribingToPresentities(sipUris);
            }
        }

        public void UnsubscribeToContactsPresence()
        {
            System.Collections.ObjectModel.Collection<string> sipUris = _cgPresenceView.GetPresentities();
            if (sipUris != null)
            {
                _cgPresenceView.StartUnsubscribingToPresentities(sipUris);
            }
        }

        /// <summary>
        /// Refresh the presence subscription to the contacts.
        /// </summary>
        public void RefreshContactsPresence()
        {
            // Synchronizing an asynchronous call.
            _cgPresenceServices.EndRefreshRemotePresenceViews(
                _cgPresenceServices.BeginRefreshRemotePresenceViews(null, null));
        }

        /// <summary>
        /// Query the specified categories published by every contact in the contact list.
        /// </summary>
        /// <param name="categoryNames">Category names</param>
        public void QueryContactsPresence(string[] categoryNames)
        {
            System.Collections.ObjectModel.Collection<string> sipUris = 
                _cgPresenceView.GetPresentities();

            // Synchronizing an asynchronous call.
            _cgPresenceServices.EndPresenceQuery(
                _cgPresenceServices.BeginPresenceQuery(sipUris, categoryNames,
                     ContactPresenceNotificationReceivedEventHandler, null, null));
        }

        /// <summary>
        /// Query the specified categories published by the specified contacts
        /// </summary>
        /// <param name="sipUris">SIP URIs of the specified contacts</param>
        /// <param name="categoryNames">Category names</param>
        public void QueryContactsPresence(string[] sipUris, string[] categoryNames)
        {
            // Synchronizing an asynchronous call.
            _cgPresenceServices.EndPresenceQuery(
                _cgPresenceServices.BeginPresenceQuery(sipUris, categoryNames,
                     ContactPresenceNotificationReceivedEventHandler, null, null));
        }

        #endregion Managing contacts' presence subscription
```

## See also

#### Concepts

[Managing self-published contact lists](managing-self-published-contact-lists.md)

