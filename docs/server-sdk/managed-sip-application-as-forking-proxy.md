---
title: Managed SIP application as forking proxy
TOCTitle: Managed SIP application as forking proxy
ms:assetid: 7d076640-0dc2-4994-bb14-e4a4cd7059c4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439071(v=office.15)
ms:contentKeyID: 57096230
ms.date: 02/11/2016
mtps_version: v=office.15
---

# Managed SIP application as forking proxy

Learn how a forking proxy in a managed SIP application forwards a SIP request to multiple SIP address and returns the responses to the sender. This topic discusses the object model for the forking behavior.


**Applies to**: Lync Server 2013

## SIP forking proxy application

In Microsoft Lync Server 2013 SDK, you can use the Microsoft SIP Processing Language (MSPL) message filter to fork basic proxies.

### SIP forking proxy behavior

The following illustration shows the basic flow of a forking proxy.

![SIP Forking Proxy Transaction](images/Dn439071.SIP_Forking_Proxy_Transaction(Office.15).jpg "SIP Forking Proxy Transaction")

When a message is dispatched to the application by the MSPL script, a **RequestReceivedEventArgs** object is returned to the method inside the application that is designated by the Dispatch call. Attached to this object is a new ServerTransaction object, which contains the Request object as the **ServerTransaction.Request** property.

To fork the **Request**, clone **ServerTransaction.Request** for each recipient. First, ensure that the **ServerTransaction.EnableForking** property is set to true. If this property is set to false (the default is true), **ArgumentException** is thrown when you call **ServerTransaction.CreateBranch** again.

For each proxied request, call **ServerTransaction.CreateBranch** and then immediately call **ClientTransaction.SendRequest**, passing in the cloned **Request**.

Responses are handled asynchronously through the **ResponseReceivedEventHandler** delegate. The **ClientTransaction.ResponseReceived** event is triggered when a response for a sent **Request** is received, and the corresponding Response object is returned as the **ResponseReceivedEventArgs.Response** property.

To proxy the response, call **ServerTransaction.SendResponse,** passing in **ResponseReceivedEventArgs.Response**.

When a final response is passed to the server transaction, the object space that contains the **ServerTransaction** and its branches is automatically disposed of by the server agent, unless the **ServerTransaction.Close()** method on **ServerTransaction** was overridden.

## See also

#### Other resources

[Managed SIP Application API](managed-sip-application-api.md)

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

