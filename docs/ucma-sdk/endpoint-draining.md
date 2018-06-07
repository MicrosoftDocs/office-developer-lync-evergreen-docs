---
title: Endpoint draining
TOCTitle: Endpoint draining
ms:assetid: 983c3c61-2ac0-4d07-9e38-4ffed06d2798
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465934(v=office.15)
ms:contentKeyID: 57102428
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Endpoint draining


**Applies to:** Lync 2013 | Lync Server 2013

In Microsoft Unified Communications Managed API 4.0 and Microsoft Lync Server 2013, methods on the [ApplicationEndpoint](https://msdn.microsoft.com/en-us/library/hh384825\(v=office.15\)) class can be used to *drain* existing calls (gracefully decline incoming calls by routing them to another application instance): [BeginDrain(AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/hh348822\(v=office.15\)) and [EndDrain(IAsyncResult)](https://msdn.microsoft.com/en-us/library/hh383086\(v=office.15\)). These methods cause all incoming calls to be automatically routed to another application instance, provided that this other application instance is available and is not draining. If the targeted application instance is unavailable or is draining, the incoming calls will be declined.

Existing conversations will continue normally (including modality addition and escalation to conference), so an application may use this feature during its shutdown phase while still completing existing calls. The application can then shut down, perform maintenance as needed, and restart. After the application restarts, new calls are again routed to it.

