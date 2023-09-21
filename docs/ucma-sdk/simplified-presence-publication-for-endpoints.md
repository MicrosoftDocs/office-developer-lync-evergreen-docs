﻿---
title: Simplified presence publication for endpoints
TOCTitle: Simplified presence publication for endpoints
ms:assetid: fbf57a68-1fec-4849-aa98-4d1646f6a7eb
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466002(v=office.15)
ms:contentKeyID: 57102939
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Simplified presence publication for endpoints


**Applies to:** Lync 2013 | Lync Server 2013

Applications can opt to automatically publish presence information for user endpoints or application endpoints at the time the endpoint is established. This is especially useful for applications that publish commonly used presence categories such as state and endpoint capabilities once, as well as for those that rarely change their published information. These applications do not need to directly deal with the underlying subscription (which is managed by [LocalOwnerPresence](localownerpresence.md)).

The actual nature of the data published for each type of endpoint differs and is discussed in the subsequent sections of this topic. In addition, there are simplified APIs to maintain the presence information for the duration of the endpoint’s lifetime. This presence information is available through the endpoint’s **PresenceServices** property—[PresenceServices](https://msdn.microsoft.com/library/hh383140\(v=office.15\)) on an application endpoint, and [PresenceServices](https://msdn.microsoft.com/library/hh349242\(v=office.15\)) on a user endpoint. These properties are references, respectively, to [ApplicationEndpointPresenceServices](https://msdn.microsoft.com/library/hh384612\(v=office.15\)) and [UserEndpointPresenceServices](https://msdn.microsoft.com/library/hh383690\(v=office.15\)) objects.

To "bootstrap" (publish initial presence information automatically when the endpoint is established), the **AutomaticPresencePublicationEnabled** property on the settings object ([UserEndpointSettings](https://msdn.microsoft.com/library/hh383789\(v=office.15\)) for user endpoints and [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) for application endpoints) should be set to true and the data to be published should be provided. If no data is specified, a default behavior is assumed. If for any reason there is an exception during the publication process (such as when the user services cluster in the enterprise is down), the establishment process is allowed to continue and publication is retried after a specified duration (about 15 minutes unless the registrar requests a different duration).

Applications that require the actual state of the auto-publishing request can track the [AutomaticPublicationState](https://msdn.microsoft.com/library/hh381788\(v=office.15\)) property on a [LocalOwnerPresence](https://msdn.microsoft.com/library/hh382370\(v=office.15\)) object, or can register for notification when the [AutomaticPublicationStateChanged](https://msdn.microsoft.com/library/hh382264\(v=office.15\)) event is raised. A value of **Published** for the **AutomaticPublicationState** property indicates successful publication, while a value of **WaitingForRetry** indicates that the publication operation will be retried.

## Publishing presence for a UserEndpoint

For user endpoints, setting the [AutomaticPresencePublicationEnabled](https://msdn.microsoft.com/library/hh381558\(v=office.15\)) property to true in the settings object causes the following actions to be taken.

  - Subscribe to **LocalOwnerPresence** and potentially bootstrap the endpoint owner's containers with default presence publications and container memberships, as determined by the server manifest. For more information, see [Unified Communications Enhanced Presence Schemas for Lync Server 2013 Documentation](https://msdn.microsoft.com/library/jj265607\(v=office.15\)).

  - Publish an initial endpoint state of **EndpointOnline**, a static value of the [PresenceState](https://msdn.microsoft.com/library/hh350296\(v=office.15\)) class. In addition, publish a user presence state, provided that **UserEndpointSettings.Presence.UserPresenceState** is non-null.

  - Publish the endpoint's basic device capabilities, as specified by the [PreferredServiceCapabilities](https://msdn.microsoft.com/library/hh382547\(v=office.15\)) property, if supported by the underlying platform. No device capabilities are published if **PreferredServiceCapabilities** is set to null. This property can be accessed from the [Presence](https://msdn.microsoft.com/library/hh383073\(v=office.15\)) property on a [UserEndpointSettings](https://msdn.microsoft.com/library/hh383789\(v=office.15\)) instance.

In the event of any exception being thrown during publication, all of the preceding steps are repeated.

In UCMA 4.0, presence state values can be modified by the use of the following methods on the [PresenceServices](https://msdn.microsoft.com/library/hh384331\(v=office.15\)) property on the endpoint.

  - [BeginUpdatePresenceState(PresenceState, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh384883\(v=office.15\))

  - [EndUpdatePresenceState(IAsyncResult)](https://msdn.microsoft.com/library/hh383446\(v=office.15\))

  - [BeginDeleteUserPresenceState(AsyncCallback, Object)](https://msdn.microsoft.com/library/hh349326\(v=office.15\))

  - [EndDeleteUserPresenceState(IAsyncResult)](https://msdn.microsoft.com/library/hh384306\(v=office.15\))

In addition, the [LocalOwnerPresence](https://msdn.microsoft.com/library/hh348476\(v=office.15\)) property on an endpoint provides access to a [LocalOwnerPresence](https://msdn.microsoft.com/library/hh382370\(v=office.15\)) object, which has methods and properties that can be used for more advanced scenarios.

## Publishing Presence for an ApplicationEndpoint

UCMA 4.0 has simplified APIs for bots or automata applications that are intended to persist their presence information because they rarely change. Such applications must set the [AutomaticPresencePublicationEnabled](https://msdn.microsoft.com/library/hh381653\(v=office.15\)) property on the [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) object to true and must provide any optional information that is to be published. The following categories are automatically published to container 0. For more information about containers, see "Containers and Categories Used by Microsoft Lync" in [Unified Communications Enhanced Presence Schemas for Lync Server 2013 Documentation](https://msdn.microsoft.com/library/jj265607\(v=office.15\)).

  - [ContactCard](https://msdn.microsoft.com/library/hh382040\(v=office.15\)) with the [IsAutomatedService](https://msdn.microsoft.com/library/hh384257\(v=office.15\)) property set to true and optionally, the [PresentityType](https://msdn.microsoft.com/library/hh365984\(v=office.15\)) and [Description](https://msdn.microsoft.com/library/hh349834\(v=office.15\)) properties on the [ApplicationEndpointPresenceSettings](https://msdn.microsoft.com/library/hh161759\(v=office.15\)) instance.

  - An aggregate state as dictated by the [InitialPresenceState](https://msdn.microsoft.com/library/hh348503\(v=office.15\)) property on an [ApplicationEndpointPresenceSettings](https://msdn.microsoft.com/library/hh161759\(v=office.15\)) instance. If no state is specified, **PersistentOnline** (a static value of the **PresenceState** class) is published.

  - A [Services](https://msdn.microsoft.com/library/hh385140\(v=office.15\)) category instance that specifies the platform-supported capabilities dictated by the [PreferredServiceCapabilities](https://msdn.microsoft.com/library/hh382547\(v=office.15\)) property on the [Presence](https://msdn.microsoft.com/library/hh381941\(v=office.15\)) property on the [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) object.

In the event of an exception being thrown during publication, all of the preceding steps are repeated. The values in the preceding list can be accessed through the **PresenceServices** property on the endpoint after endpoint establishment.

UCMA 4.0 allows the [PresentityType](https://msdn.microsoft.com/library/hh365599\(v=office.15\)) and [Description](https://msdn.microsoft.com/library/hh348857\(v=office.15\)) properties of a **ContactCard** instance to be modified, provided that automatic presence publication is enabled. The [UpdatePublishedData(String, String)](https://msdn.microsoft.com/library/hh382724\(v=office.15\)) method on the [PresenceServices](https://msdn.microsoft.com/library/hh383140\(v=office.15\)) property can be used for this purpose.

In the following example, an [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)) instance is created and initialized with several properties on an [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) instance that are appropriate for a bot.

```csharp
ApplicationEndpointSettings endpointSettings = new ApplicationEndpointSettings("sip:bot@contoso.com");
endpointSettings.AutomaticPresencePublicationEnabled = true;
endpointSettings.Presence.PresentityType = "automaton";
endpointSettings.Presence.Description = "this is a test bot";
endpointSettings.PreferredServiceCapabilities.InstantMessagingSupport = CapabilitySupport.Supported;
ApplicationEndpoint endpoint = new ApplicationEndpoint(platform, endpointSettings);
```

