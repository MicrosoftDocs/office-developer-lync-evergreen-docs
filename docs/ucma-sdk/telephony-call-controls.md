---
title: Telephony call controls
TOCTitle: Telephony call controls
ms:assetid: 692373af-0f58-4dc9-8f60-da4557106ae5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465956(v=office.15)
ms:contentKeyID: 57102447
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Telephony call controls


**Applies to:** Lync 2013 | Lync Server 2013

Microsoft Unified Communications Managed API 4.0 provides for basic telephony call control actions, including forwarding, acceptance/decline, and message sending. With UCMA 4.0, an application can place calls to unified communications-enabled endpoints and PSTN targets, transfer calls between itself and other entities, and route calls to agent hunting pools.

  - Call establishment
    
    UCMA 4.0 allows an application to reach out with outbound notifications, take actions on behalf of a user, or as a client, to a far-end that is a UC-capable endpoint, and create and manage multiple modalities (audio, IM) as well as providing the ability for an application to extend the default modalities for custom media (such as whiteboarding). From the time that an application establishes its first endpoint, it can place and receive calls in the Microsoft Lync Server 2013 system.

  - Call acceptance, call declining, call transfer, and call deflection
    
    UCMA 4.0 provides the application the ability to receive new incoming calls, both audio and Instant Messaging. An application can then accept or decline a call, or transfer it to another recipient for ultimate call handling. For more information, see [Accepting an incoming call](accepting-an-incoming-call.md) and [Transferring a call](transferring-a-call.md).

  - Presence-based call routing
    
    When the UCMA 4.0/Microsoft Lync 2013 solution is used to route calls, presence is used on the recipient’s side to assist in routing to an endpoint of an available user. Further, presence can be used by applications to signal availability for calls to end users. For more information, see [Calls, flows, conversations, and MCU sessions](calls-flows-conversations-and-mcu-sessions.md).

In UCMA 4.0, a number of other new call-centric features have been added, including the ability for an application to park a call (see [Call park](call-park.md)), use a back-to-back agent (see [Back-to-back user agent](back-to-back-user-agent.md)), send and receive rich contextual information (see [Conversation context channel](conversation-context-channel.md)), and interoperate with PSTN voice calls (see [PSTN gateway and IP-PBX interoperability](pstn-gateway-and-ip-pbx-interoperability.md)).

