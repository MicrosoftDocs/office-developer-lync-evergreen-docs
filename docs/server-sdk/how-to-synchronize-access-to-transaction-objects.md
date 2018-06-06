---
title: 'How to: Synchronize access to transaction objects'
TOCTitle: 'How to: Synchronize access to transaction objects'
ms:assetid: cf82601c-20bf-4ff5-aa13-9be1ca8d11c9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439086(v=office.15)
ms:contentKeyID: 57096263
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Synchronize access to transaction objects

Learn how to synchronize access to transaction objects in a Microsoft Lync Server 2013 deployment.


_**Applies to:** Lync Server 2013_

## Synchronizing access to transaction objects

The server agent maintains several objects for the application. In many situations, an application can access these objects from multiple threads. To guarantee safe access, the applications should participate in a predefined resource locking scheme.

The server agent guarantees that two threads will not at the same time run separate handlers for messages that belong to the same transaction by serializing the message stream of each transaction internally, according to the order in which the messages were received. The server agent also obtains and releases all appropriate transaction locks. Therefore, if an application consists only of message handlers (it is a Microsoft SIP Processing Language (MSPL) script or does not run any code that is outside the dispatch handling methods), synchronization is handled completely by the server agent and no specific implementation is needed within the application.

Also, if applications queue internal work items that are serviced asynchronously, they must acknowledge the locks that are implemented by the class library. The server agent still handles the acquisition and release of all locks for message handler calls, and applications have to synchronize with the server agent only when they are not running message handlers for the transaction objects.

All objects that are related to a server transaction share a common lock. For a forking proxy, all of the branch client transactions share this common locked space with the original server transaction. Any application that references an object within this common space and is outside the dispatch handler should lock it first. The reference to this common space is obtained from the [SyncRoot](https://msdn.microsoft.com/en-us/library/jj266173\(v=office.15\)) property on the respective [ClientTransaction](https://msdn.microsoft.com/en-us/library/jj265716\(v=office.15\)) or [ServerTransaction](https://msdn.microsoft.com/en-us/library/jj265462\(v=office.15\)) instance.

## See also

#### Concepts

[Managed SIP Application API](managed-sip-application-api.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

