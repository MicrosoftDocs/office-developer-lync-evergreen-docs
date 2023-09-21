---
title: Session dialog resiliency
TOCTitle: Session dialog resiliency
ms:assetid: 20d6e2ea-0d2b-46ef-a35e-7ce77dc282fd
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465939(v=office.15)
ms:contentKeyID: 57102433
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Session dialog resiliency


**Applies to:** Lync 2013 | Lync Server 2013

Session Dialog Resiliency (SDR) refers to the ability of a call to resolve and repair a route failure or the temporary inability to reach a remote endpoint. These problems are usually caused by temporary breaks in signaling paths due to intermediate server or temporary remote endpoint connectivity issues. After detecting a break, the signaling layer attempts to locate a new path (by way of any allowed Microsoft Lync Server 2013 servers) and re-establish communications. (Media can often flow uninterrupted, as media is negotiated peer-to-peer, not via the server; if broken, media will also attempt to relocate a path).

While Microsoft Unified Communications Managed API (UCMA) 2.0 supported SDR, in Microsoft Unified Communications Managed API 4.0 an application can fully participate in the SDR process, and can be aware of the recovery at a more detailed level. Further, in UCMA 4.0, the application is more likely to recover, and to recover more quickly. In UCMA 2.0, when the route was broken, UCMA 2.0 would often wait passively for healing attempts from the remote end. In contrast, UCMA 4.0 actively attempts to recover the route.

Dialog Recovery in UCMA 4.0 adheres to the principle "Succeed or fail quickly, recover forever." In the case of a dialog route issue, UCMA 4.0 will resend the message if the dialog can be repaired immediately (a 430 (Flow Failed) response with a "Dialog Route Set Update" header), as shown in the following flow diagram.

![Dialog resiliency 1](images/Dn465939.UCMA-DialogResiliency1(Office.15).jpg "Dialog resiliency 1")

Otherwise UCMA 4.0 alerts the sender that the message has failed, raises a substate changed event, and immediately begins trying to recover the route. While the route is broken, session timers are paused.

UCMA 4.0 can heal a route in either of two ways:

  - When the route is broken, UCMA 4.0 continually sends route-healing UPDATEs, which will heal the route (and causes a substate change on success (200-OK reply). The following illustration shows the message flow for this case.
    
    UCMA heals the route in a long-lived failure
    
      
    ![Dialog resiliency 2a](images/Dn465939.UCMA-DialogResiliency2a(Office.15).jpg "Dialog resiliency 2a")

  - Alternatively, if UCMA 4.0 receives a route-healing UPDATE from the far end, the route will be restored, and a 200-OK message is sent, as shown in the following message flow diagram.
    
    ![Dialog resiliency 2b](images/Dn465939.UCMA-DialogResiliency2b(Office.15).jpg "Dialog resiliency 2b")

The session timer also can take part in route healing when it discovers a route failure. The following illustration shows the message flow for this case.

![Dialog resiliency 3](images/Dn465939.UCMA-DialogResiliency3(Office.15).jpg "Dialog resiliency 3")

UCMA can ask that the response code come from the remote endpoint, as shown in the following illustration.

![Dialog resiliency 4](images/Dn465939.UCMA-DialogResiliency4(Office.15).jpg "Dialog resiliency 4")

In most cases, the application needs only to be aware of the fact that some operations can fail during the time the route recovery is in progress, and to post log entries as appropriate to the application's usage model until the substate indicates the recovery of the route. If the break affects the media path, it may lead to call termination if the path remains unresponsive for more than 15 minutes. For more information, see [Call recovery](call-recovery.md).

