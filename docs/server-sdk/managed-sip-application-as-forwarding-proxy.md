---
title: Managed SIP application as forwarding proxy
TOCTitle: Managed SIP application as forwarding proxy
ms:assetid: 353e7047-7001-4c5d-8496-fb4ea4ad8a31
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439070(v=office.15)
ms:contentKeyID: 57096228
ms.date: 02/11/2016
mtps_version: v=office.15
---

# Managed SIP application as forwarding proxy

Learn how a forwarding proxy in a managed SIP application forwards a SIP request to a single SIP address and returns the responses to the sender. This topic discusses the object model for the forwarding behavior.


**Applies to**: Lync Server 2013

## SIP forwarding proxy application

In Microsoft Lync Server 2013 SDK, you can use the Microsoft SIP Processing Language (MSPL) message filter to forward basic proxies in a managed SIP application.

### SIP forwarding proxy behavior

The following illustration shows the basic flow of a forwarding proxy.

![SIP Simple Forwarding Proxy Transaction](images/Dn439070.SIP_Simple_Forwarding_Proxy_Transaction(Office.15).jpg "SIP Simple Forwarding Proxy Transaction")

When a message is dispatched to the application by the MSPL script, a **RequestReceivedEventArgs** object is returned to the method inside the application that is designated by the **Dispatch** call. Attached to this object is a new **ServerTransaction** object, which contains the **Request** object as the **ServerTransaction.Request** property.

The **Request** forwarding process starts by starting a single branch with a call to **ServerTransaction.CreateBranch**. After that, call **ClientTransaction.SendRequest**, passing in the cloned **Request**.

Responses are handled asynchronously through the **ResponseReceivedEventHandler** delegate. The **ClientTransaction.ResponseReceived** event is triggered when a response for a sent **Request** is received, and the corresponding **Response** object is returned as the **ResponseReceivedEventArgs.Response** property.

To proxy the response, call **ServerTransaction.SendResponse**, passing in **ResponseReceivedEventArgs.Response**.

When responses have been received for the forwarded request, the object space that contains the **ServerTransaction** instance and its sole branch is automatically disposed of by the server agent, unless the **ServerTransaction.Close()** method on **ServerTransaction** is specifically overridden and contains post-transaction directives.

## See also

#### Other resources

[Managed SIP Application API](managed-sip-application-api.md)

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

