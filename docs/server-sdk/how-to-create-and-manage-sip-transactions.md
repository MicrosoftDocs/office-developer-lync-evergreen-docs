---
title: 'How to: Create and manage SIP transactions'
TOCTitle: 'How to: Create and manage SIP transactions'
ms:assetid: 1178fb0a-434c-4924-a386-797da894c301
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439083(v=office.15)
ms:contentKeyID: 57096240
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Create and manage SIP transactions

Learn how to use the [Transaction](https://msdn.microsoft.com/en-us/library/jj265742\(v=office.15\)) class to create and manage SIP transactions in a Microsoft Lync Server 2013 deployment.


**Applies to**: Lync Server 2013

## Creating and managing SIP transactions

The [Microsoft.Rtc.Sip](https://msdn.microsoft.com/en-us/library/jj266253\(v=office.15\)) namespace defines a base type, [Transaction](https://msdn.microsoft.com/en-us/library/jj265742\(v=office.15\)), that represents the basic properties that are used in a SIP transaction. This includes the request that started the transaction, responses that are handled by the transaction, and events that are used to catch transaction status changes (such as time-out events or cancellations).

The following types are derived from the **Transaction** class:

  - The [ClientTransaction](https://msdn.microsoft.com/en-us/library/jj265716\(v=office.15\)) instance represents a client transaction.

  - The [ServerTransaction](https://msdn.microsoft.com/en-us/library/jj265462\(v=office.15\)) instance represents a server transaction.

The **ServerTransaction** instance is obtained by referencing the [ServerTransaction](https://msdn.microsoft.com/en-us/library/jj265472\(v=office.15\)) property on the [RequestReceivedEventArgs](https://msdn.microsoft.com/en-us/library/jj265762\(v=office.15\)) instance, when a **RequestReceivedEventArgs** object is dispatched to the designated method. The request it was created to service can be obtained by using one of the following properties:

  - The RequestReceivedEventArgs; [Request](https://msdn.microsoft.com/en-us/library/jj265724\(v=office.15\)) property

  - **Request()**

Client transactions must be created programmatically by calling [CreateBranch()](https://msdn.microsoft.com/en-us/library/jj265503\(v=office.15\)) on the [ServerTransaction](https://msdn.microsoft.com/en-us/library/jj265462\(v=office.15\)). The UAC case, where a client transaction originates a request and does not have a parent server transaction, is not supported.

To fork a message, **ServerTransaction.CreateBranch** can be called as many times as forks are needed. To send a request to each fork, call [SendRequest(Request)](https://msdn.microsoft.com/en-us/library/jj266211\(v=office.15\)) on each branch.

Responses to serviced requests are obtained by registering a handler for the [ResponseReceived](https://msdn.microsoft.com/en-us/library/jj266796\(v=office.15\)) event. When this event is raised, any response that is received by Lync Server 2013 that matches the originating request is sent as a [ResponseReceivedEventArgs](https://msdn.microsoft.com/en-us/library/jj266293\(v=office.15\)) object to the method registered by using the [ResponseReceivedEventHandler](https://msdn.microsoft.com/en-us/library/jj265708\(v=office.15\)) delegate.

Responses can also be raised by using dispatches from the message filter script when it is set to filter responses. In this case, the response will be out-of-context because there is no **ClientTransaction** object on the server that originated the request. In this case, the new **ClientTransaction** object is obtained by referencing the [ClientTransaction](https://msdn.microsoft.com/en-us/library/jj265494\(v=office.15\)) property on the [ResponseReceivedEventArgs](https://msdn.microsoft.com/en-us/library/jj266293\(v=office.15\)) instance. The server transaction that forwards the response is obtained by referencing the [ServerTransaction](https://msdn.microsoft.com/en-us/library/jj265793\(v=office.15\)) property on this **ClientTransaction** instance, which contains the new **ServerTransaction** instance to handle it.

If a **CANCEL** method is received for a transaction, the [Canceled](https://msdn.microsoft.com/en-us/library/jj265710\(v=office.15\)) event is raised. When the transaction is closed, [Terminated](https://msdn.microsoft.com/en-us/library/jj265709\(v=office.15\)) is raised. If a transaction times out, [TimedOut](https://msdn.microsoft.com/en-us/library/jj266758\(v=office.15\)) is raised.

## See also

#### Concepts

[Managed SIP Application API](managed-sip-application-api.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

