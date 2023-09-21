---
title: Preparing for category publications
TOCTitle: Preparing for category publications
ms:assetid: 5c56c317-9710-450a-8c13-27146df9d806
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454650(v=office.15)
ms:contentKeyID: 57092902
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Preparing for category publications


**Applies to:** Lync 2013 | Lync Server 2013

In Microsoft Unified Communications Managed API 4.0, presence publication is managed by using the LocalOwnerPresence class. An instance of this class is the starting point to execute and manage presence publications. The supported operations include the following:

  - Setting or modifying the access control list in a container.

  - Publishing or deleting specified presence category instances.

  - Subscribing to self-published category instances, useful to roam user-specific data across multiple endpoints, among other things.

  - Receiving change notifications in categories publication.

  - Receiving change notifications in self-subscription states.

  - Receiving change notifications in container memberships.

  - Receiving change notifications in presence watcher list.

  - Acknowledging specified presence watchers.

Before performing any of such operations, you must first obtain an instance of this type from the established LocalEndpoint instance and prep the LocalOwnerPresence object to suit your application needs. The following code snippet offers an example of what is involved in such preparation.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using Microsoft.Rtc.Collaboration;
using Microsoft.Rtc.Collaboration.Presence;
using Microsoft.Rtc.Sdk.Categories;
using UcmaAppLibrary;

namespace PresencePublisher
{
    public class UcmaPublisher : UcmaObject
    {
        LocalOwnerPresence _localPresence;
        

        public UcmaPublisher(LocalEndpoint lp)
        {
            _localPresence = lp.LocalOwnerPresence;

            _localPresence.SubscriptionStateChange += new EventHandler<PresenceSubscriptionStateChangedEventArgs>(_localPresence_SubscriptionStateChange);
            _localPresence.PresenceNotificationReceived += new EventHandler<LocalPresentityNotificationEventArgs>(_localPresence_PresenceNotificationReceived);
            _localPresence.SubscriberNotificationReceived += new EventHandler<SubscriberNotificationEventArgs>(_localPresence_SubscriberNotificationReceived);

            // Subscribe to self-presence and self-usage categories
            _localPresence.EndSubscribe(_localPresence.BeginSubscribe(null, null));
        }

        void _localPresence_SubscriberNotificationReceived(object sender, SubscriberNotificationEventArgs e)
        {
            if (OnSubscriberNotificationReceived != null)
                RaiseEvent(OnSubscriberNotificationReceived, this, e);
        }


        void _localPresence_SubscriptionStateChange(object sender, PresenceSubscriptionStateChangedEventArgs e)
        {
            if (OnSubscriptionStateChanged != null)
                RaiseEvent(OnSubscriptionStateChanged, this, e);
        }

        void _localPresence_PresenceNotificationReceived(object sender, LocalPresentityNotificationEventArgs e)
        {
            List<PresenceState> stateList = new List<PresenceState>();
            if (e.AggregatedPresenceState != null)
                stateList.Add(e.AggregatedPresenceState);
            if (e.EndpointPresenceState != null)
                stateList.Add(e.EndpointPresenceState);
            if (e.UserPresenceState != null)
                stateList.Add(e.UserPresenceState);

            List<Note> noteList = new List<Note>();
            if (e.PersonalNote != null)
                noteList.Add(e.PersonalNote);
            if (e.OutOfOfficeNote != null)
                noteList.Add(e.OutOfOfficeNote);

            Services services = e.ServiceCapabilities;

            ContactCard contactCard = e.ContactCard;
            if (OnSelfPresenceNotificationReceived != null)
                RaiseEvent(OnSelfPresenceNotificationReceived, this,
                    new SelfPresenceNotificationEventArgs(stateList.ToArray(), noteList.ToArray(), services, contactCard));

            if (OnAllCategoriesReceived != null)
                RaiseEvent(OnAllCategoriesReceived, this, new CategoriesNotificationEventArgs(e.AllCategories));


            if (OnSelfUsageCategoriesReceived != null)
                RaiseEvent(OnSelfUsageCategoriesReceived, this, new CategoriesNotificationEventArgs(e.SelfUsageCategories));

        }


    }
}
```

In this example, the preparation for publication is carried out in the constructor of the UcmaPublisher class and involves mostly registering for the SubscriptionStateChange, PresenceNotificationReceived, and SubscriberNotificationReceived events. The registration enables the application to receive change notifications in the self-subscription, to receive newly published or modified category instances, and to be alerted of a pending subscriber, respectively. For the application to actually receive such events, the self-subscription must be started. This is accomplished by the call to the BeginSubscribe/EndSubscribe on the localOwnerPresence object.

The application is responsible for handling the events. Here, the required event handlers are \_localPresence\_SubscriptionStateChange, \_localPresence\_PresenceNotificationReceived and \_localPresence\_SubscriberNotificationReceived, respectively. The received data is propagated to the caller of the UcmaPublisher object.

## See also

#### Concepts

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

