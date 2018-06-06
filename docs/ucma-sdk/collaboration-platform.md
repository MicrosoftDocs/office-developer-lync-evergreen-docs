---
title: Collaboration platform
TOCTitle: Collaboration platform
ms:assetid: bad16211-f49a-4897-a978-14345082898c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465954(v=office.15)
ms:contentKeyID: 57102445
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Collaboration platform


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
Connection management  
Managing trust with Lync Server  
Extensible communication framework  
Auto-provisioning  

The collaboration platform, an instance of the [CollaborationPlatform](https://msdn.microsoft.com/en-us/library/hh385176\(v=office.15\)) class, provides capabilities for managing connections to and from the platform, guarantees a trust relationship with Microsoft Lync Server 2013 for server-mode **CollaborationPlatform** instances, and provides a mechanism whereby developers can extend the capabilities of the platform beyond the built-in media types that are supported in Microsoft Unified Communications Managed API 4.0.

Depending on the constructor used, a **CollaborationPlatform** instance is created either as a client platform or as a server platform. A typical use for a client platform is to permit the creation of a number of clients that can be used to simulate users connected to an application.

The endpoints in a UCMA application share various settings, resources, and services, all of which are managed by the **CollaborationPlatform**. These services are made possible by shared resources such as the SIP stack, and include connection management, message routing to individual endpoints, and endpoint auto-provisioning. Shared settings such as the trusted GRUU and user agent enable endpoints to construct messages in a uniform manner throughout the application. Media extensions registered with the **CollaborationPlatform** enable endpoints to handle media types other than those built into UCMA.

## Connection management

The connection manager encapsulates the SIP stack and is used to provide services for endpoints. Each platform is associated with a single connection manager that endpoints can use. The connection manager provides connection sharing, certificate management, and takes care of outgoing and incoming connections for the endpoint. In UCMA 4.0 there are three nonabstract connection manager types: a client connection manager and two server connection managers, with one of the server connection managers using TCP as the transport type, and the other server connection manager using TLS as the transport type. For more information, see [Connection manager](connection-manager.md).

The **CollaborationPlatform** class exposes the connection manager through its [ConnectionManager](https://msdn.microsoft.com/en-us/library/hh384799\(v=office.15\)) property. Using this property, an application can enforce connection policy and provide connection throttling, ensure that incoming connections come from trusted servers, and host authentication authority.

The following illustration shows the relationship between a UCMA 4.0 application and Lync Server 2013.

![Connection Manager](images/Dn465954.UCMA-Connections(Office.15).jpg "Connection Manager")

## Managing trust with Lync Server

When the **CollaborationPlatform** instance is created, a trusted GRUU is assigned to it, which ensures that the platform is trusted at the SIP level (that is, by the SIP stack). To confer this trust relationship, Lync Server 2013 reads the Active Directory trusted service object (**msRTCSIP-TrustedService**) and assigns the associated GRUU to the platform. This GRUU is tied to a particular FQDN and port combination. For more information, see [Activating a UCMA 4.0 trusted application](activating-a-ucma-4-0-trusted-application.md). Because only one process on a computer can listen on a given port, only one process can use the trusted GRUU—the process that is allowed to listen on that port.

## Extensible communication framework

The **CollaborationPlatform** contains all of the factories that are required for the media types supported in UCMA 4.0. In other words, factories for the [InstantMessagingCall](https://msdn.microsoft.com/en-us/library/hh161841\(v=office.15\)), **InstantMessagingProvider**, [AudioVideoCall](https://msdn.microsoft.com/en-us/library/hh383901\(v=office.15\)), and **AudioVideoProvider** classes are already registered with **CollaborationPlatform**. Developers who wish to implement custom media types can do so by creating custom call and media provider classes that inherit from, respectively, the [Call](https://msdn.microsoft.com/en-us/library/hh384235\(v=office.15\)) and [MediaProvider](https://msdn.microsoft.com/en-us/library/hh383767\(v=office.15\)) abstract base classes. For more information, see the topics in [Extending the UCMA platform](extending-the-ucma-platform.md).

## Auto-provisioning

A **CollaborationPlatform** instance for a trusted server application can be initialized for auto-provisioning. Such a platform instance reads the configuration for the trusted application and its endpoints from Lync Server 2013 Central Management Store and Active Directory, and initializes UCMA with this configuration data. The platform instance also keeps track of certain changes in the configuration data and notifies the application of them, as necessary.

