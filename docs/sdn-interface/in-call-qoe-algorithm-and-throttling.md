---
title: In-call QoE algorithm and throttling
TOCTitle: In-call QoE algorithm and throttling
ms:assetid: 121925d4-7a91-473e-b0b8-f282e4e78dd2
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785196(v=office.15)
ms:contentKeyID: 62952680
ms.date: 02/16/2015
mtps_version: v=office.15
---

# In-call QoE algorithm and throttling

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

Lync clients can now send call and quality data and the Lync SDN Manager (LSM) processes and forwards the data during a call instead of only after the end of the call.

The InCallQuality events are sent according to an algorithm in the media stack of the Lync Client, which determines changes to the quality of the call. When these events are raised independently for several categories and levels for each stream, creating an InCallQuality message for each of these events might flood a network that we attempt to improve. To prevent this, we have implemented a throttling algorithm in which InCallQuality messages are not sent with every occurrence of an event. The throttlingperiod time is between at least two of these messages. A message might report multiple quality changes to the stream since the previous message. The LSM will determine the overall state of the stream from the values and history provided.

Even in a high quality network without Lync raising any quality related events, the client will send an InCallUpdate message after the first throttlingperiod. This will enable the Network Controllers to receive several call- or stream-related metrics and configurations during the call. Similarly, the LSM will send an IncallQuality message after demoting an Audio-Video call to Audio-only call. In this scenario, however, no end-of-call QualityUpdate message will be sent for the terminated Video streams.

