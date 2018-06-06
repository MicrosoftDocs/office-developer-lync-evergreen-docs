---
title: 'How to: Manage server agent object lifetimes'
TOCTitle: 'How to: Manage server agent object lifetimes'
ms:assetid: 13526dfd-050a-4cbc-b8cf-e36b81e12f50
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439084(v=office.15)
ms:contentKeyID: 57096241
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Manage server agent object lifetimes

Learn how to manage server agent object lifetimes in a Microsoft Lync Server 2013 deployment.


_**Applies to:** Lync Server 2013_

## Managing server agent object lifetimes

The server agent maintains the lifetimes of several SIP-specific objects that are defined by classes in the [Microsoft.Rtc.Sip](https://msdn.microsoft.com/en-us/library/jj266253\(v=office.15\)) namespace.

For example, when a transaction is terminated, the server agent releases not only the corresponding [Transaction](https://msdn.microsoft.com/en-us/library/jj265742\(v=office.15\)) object, but also releases the [Request](https://msdn.microsoft.com/en-us/library/jj266237\(v=office.15\)) object for that transaction and any associated [Response](https://msdn.microsoft.com/en-us/library/jj266760\(v=office.15\)) objects.

This issue is independent of the garbage collection that the .NET Framework common language runtime (CLR) performs. All classes whose instances have controllable lifetimes implement the standard **IDisposable** interface, which enables application control of the object lifetime that are independent of the CLR. Because many SIP objects such as transactions have no reason to persist after they are processed, reclaiming their resources immediately improves efficiency and performance. This occurs with a call from the server agent object to the implementation of the **Close()** method on the object whose resources must be deallocated.

The base implementation of **Close()** on the **Transaction** class merely invokes a virtual implementation of the **IDisposable.Dispose()** method. Any class that extend the [ServerTransaction](https://msdn.microsoft.com/en-us/library/jj265462\(v=office.15\)) or [ClientTransaction](https://msdn.microsoft.com/en-us/library/jj265716\(v=office.15\)) instance can also override **Close()** with an application-specific implementation that extends the life of the transactions as needed.

Any overriding implementation of **Close()** must ensure that **Dispose()** is called after the event is processed or incur a possible performance penalty.

## See also

#### Concepts

[Managed SIP Application API](managed-sip-application-api.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

