﻿---
title: User endpoints and application endpoints
TOCTitle: User endpoints and application endpoints
ms:assetid: f032f3b0-9dd1-4472-b615-75b83fd6c40f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466053(v=office.15)
ms:contentKeyID: 57103046
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# User endpoints and application endpoints


**Applies to:** Lync 2013 | Lync Server 2013

 

The [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)) class is an endpoint type that is principally used by server applications, and that provides communication and collaboration services for end users.

The [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\)) class is an endpoint type that is primarily used to represent an endpoint for a user with a SIP identity.

Each of the preceding endpoint types is derived from the abstract [LocalEndpoint](https://msdn.microsoft.com/library/hh349887\(v=office.15\)) class. Although it's possible to create a class derived from **LocalEndpoint**, developers should not attempt to do so, but should instead use the **UserEndpoint** and **ApplicationEndpoint** classes.

## ApplicationEndpoint

The information in this section is concerned with concepts that apply to the **ApplicationEndpoint** type.

### Instantiation

**ApplicationEndpoint** instances can be created only against server-mode [CollaborationPlatform](https://msdn.microsoft.com/library/hh385176\(v=office.15\)) objects. On a manually-provisioned **CollaborationPlatform**, the [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) object, which is needed to initialize the endpoint, must be created and populated by the application. An auto-provisioned **CollaborationPlatform** instance automatically discovers the application endpoint settings that are configured for the application and invokes the handler passed to the [RegisterForApplicationEndpointSettings(EventHandler\<ApplicationEndpointSettingsDiscoveredEventArgs\>)](https://msdn.microsoft.com/library/hh385027\(v=office.15\)) method on the **CollaborationPlatform** instance. Also, if the settings are deleted for an auto-provisioned application endpoint, the endpoint is automatically terminated.

An **ApplicationEndpoint** instance can optionally register with a Microsoft Lync Server 2013 registrar if it must publish presence uniquely for each endpoint. However, application endpoints with the same URI for different application instances typically are equivalent. As a result, application endpoints need to publish presence for the URI to which they correspond rather than for each individual endpoint. An application endpoint can turn off registration by setting the [UseRegistration](https://msdn.microsoft.com/library/hh384976\(v=office.15\)) property on the **ApplicationEndpointSettings** instance to false.

### Routing basics

A Contact object in Active Directory enables Lync Server 2013 to route messages to an application endpoint. An application can be deployed on a single server or a pool of servers. When servers are deployed in a pool, each computer in the pool runs an instance of the application. Each application instance has an application endpoint that corresponds to the Contact object that the application is configured with. When a message arrives, targeting the URI or phone URI of a Contact object, the Lync Server 2013 routing logic can look up the FQDN of the pool of servers on which the application is deployed. The message is then dispatched, by means of DNS-based load balancing, to the address of one of the servers in the pool. For more information about DNS-based load balancing, see [General application activation](general-application-activation.md).

While users access a service by the well-known URIs of its endpoints, trusted applications can be reached by targeting the GRUU of a pool where an application is deployed. An application can discover the pool GRUU of another application if the application ID is known. The [GetApplicationTopologyData(String)](https://msdn.microsoft.com/library/hh381419\(v=office.15\)) method on the [TopologyConfiguration](https://msdn.microsoft.com/library/hh384508\(v=office.15\)) property of a [CollaborationPlatform](https://msdn.microsoft.com/library/hh385176\(v=office.15\)) instance returns all of the pool GRUUs of an application. Only auto-provisioned applications can use this method.

### Default routing endpoint

A particular **ApplicationEndpoint** instance in an application instance can be designated as the default routing endpoint by setting the [IsDefaultRoutingEndpoint](https://msdn.microsoft.com/library/hh382661\(v=office.15\)) property to true on the [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) instance for that endpoint. If an incoming message cannot be matched uniquely to any of the endpoints in an application instance, the message is routed to the default routing endpoint, if one exists. The Contact Center sample demonstrates one aspect of this concept by having custom routing logic in the default routing endpoint. This logic causes a message to be routed to a specific endpoint when the message target is the application’s GRUU rather than an endpoint’s URI.

### Draining

Draining allows an application endpoint to be taken down gracefully without calls being dropped. When a computer running one instance of an application needs to be stopped for maintenance or other reason, the application should call [BeginDrain(AsyncCallback, Object)](https://msdn.microsoft.com/library/hh348822\(v=office.15\)) on all the endpoints of that application instance. Each endpoint then enters the **Draining** state (a value of the [LocalEndpointState](https://msdn.microsoft.com/library/hh349164\(v=office.15\)) enumeration, and accessible through the [State](https://msdn.microsoft.com/library/hh382541\(v=office.15\)) property). In this state, new calls or calls on existing conversations are unaffected, but requests for establishing calls for new conversations are rejected with a specific error code prompting the server’s routing logic to send the request to a different application instance. As each endpoint finishes servicing the existing conversations (that is, becomes drained), the callback passed to **BeginDrain** is invoked. After an endpoint has drained, it can be terminated without losing any calls.

## UserEndpoint

The material in this section is specific to the **UserEndpoint** type.

### Instantiation

[UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\)) instances can be created from client-mode or server-mode **CollaborationPlatform** objects. When a **UserEndpoint** is established, it registers with a server running Lync Server 2013. This connection to the server is cached and is used for all outgoing communications.

When a **UserEndpoint** instance is created, a [UserEndpointSettings](https://msdn.microsoft.com/library/hh383789\(v=office.15\)) object is initialized and passed to the endpoint constructor. If the settings do not contain the FQDN of a server running Lync Server 2013, a DNS SRV query is used to discover such a server.


> [!IMPORTANT]
> <P>If a <STRONG>UserEndpoint</STRONG> is used with a server-mode <STRONG>CollaborationPlatform</STRONG> instance in a high-scale application, the application should set the <A href="https://msdn.microsoft.com/library/hh349573(v=office.15)">IsEndpointThrottled</A> property on a <STRONG>SipEndpoint</STRONG> instance to false.</P>



The following code example shows how to set the **IsEndpointThrottled** property for an existing **UserEndpoint** instance named *userEP*.

```csharp
SipEndpoint sipEP = userEP.InnerEndpoint as SipEndpoint;
sipEP.IsEndpointThrottled = false;
```

## Registration recovery

Registered endpoints of both types refresh their registrations periodically and after a connection is dropped. Because connection recovery can take time, a default number of retries is built into UCMA 4.0 to retry for a few minutes before terminating the endpoint. The [MaxRegisterRetries](https://msdn.microsoft.com/library/hh381643\(v=office.15\)) property on a [LocalEndpointSettings](https://msdn.microsoft.com/library/hh383424\(v=office.15\)) instance can be used to increase the number of retries. While retries are in progress, the endpoint is in the **Reestablishing** state, a value of the [LocalEndpointState](https://msdn.microsoft.com/library/hh349164\(v=office.15\)) enumeration.

When registration recovery is finished, existing subscriptions are refreshed automatically. If presence publications are lost because a Lync Server 2013 computer was removed from service, the [RepublishingRequired](https://msdn.microsoft.com/library/hh383031\(v=office.15\)) event might be raised. The application should handle this event by republishing its presence.

## Endpoint state transitions

The [State](https://msdn.microsoft.com/library/hh382541\(v=office.15\)) property on the **LocalEndpoint** class records the state of the endpoint. The state transitions for both endpoint types, **ApplicationEndpoint** and **UserEndpoint**, are shown in the following illustration.

![Endpoint state transitions](images/Dn466053.StateMach_AppEndpt(Office.15).jpg "Endpoint state transitions")

The state transitions in the preceding illustrations are shown in the following list:

1.  The transition from **Idle** to **Establishing** occurs when **BeginEstablish** is called.

2.  The transition from **Establishing** to **Idle** occurs when **EndEstablish** throws an exception.

3.  The transition from **Establishing** to **Established** occurs when **EndEstablish** returns successfully.

4.  The transition from **Established** to **Reestablishing** occurs when a registration refresh failure occurs due to a connection drop (applies only to registered endpoints).

5.  The transition from **Reestablishing** to **Established** occurs when the connection is restored and the registration is refreshed (applies only to registered endpoints).

6.  The transition from **Established** to **Draining** occurs when the application calls **BeginDrain** from the **Established** state (applies only to application endpoints).

7.  The transition from **Reestablishing** to **Draining** occurs when the application calls **BeginDrain** from the **Reestablishing** state (applies only to application endpoints).

8.  The transition from **Established** to **Terminating** occurs when one of the following actions takes place:
    
    - **BeginTerminate** is called.
    
    - The server deregisters the endpoint.
    
    - The contact object is deleted.

9.  The transition from **Reestablishing** to **Terminating** occurs when one of the following actions takes place (applies only to user endpoints):
    
    - **BeginTerminate** is called.
    
    - A registration refresh retry fails.
    
    - The contact object is deleted.

10. The transition from **Draining** to **Terminating** occurs when one of the following actions takes place:
    
    - **BeginTerminate** is called.
    
    - The server deregisters the endpoint.
    
    - A registration refresh retry fails.
    
    - The contact object is deleted.

11. The transition from **Idle** to **Terminating** occurs when **BeginTerminate** is called on the endpoint.

12. The transition from **Terminating** to **Terminated** occurs when termination completes.

