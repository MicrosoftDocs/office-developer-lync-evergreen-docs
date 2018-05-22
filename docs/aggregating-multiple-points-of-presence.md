---
title: Aggregating multiple points of presence
TOCTitle: Aggregating multiple points of presence
ms:assetid: 59a45fa5-7377-42b7-8ebe-e046371f7b53
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454621(v=office.15)
ms:contentKeyID: 57093180
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Aggregating multiple points of presence


_**Applies to:** Lync 2013 | Lync Server 2013_

At any time, a user may have logged on to several unified communications-enabled devices, including a mobile phone, a desk phone, a laptop and a desktop computer. The user may be talking on the mobile phone while typing on the laptop computer, leaving the desktop computer idle and the desk phone available to receive incoming calls. Each of the devices corresponds to an endpoint in a unified communications network and each can publish the endpoint-specific presence information for the user. However, a presence watcher may not be interested in the views of the endpoint-specific presence of the user. Furthermore, the user may want to present to others a single view of her or his overall presence, independent of individual endpoints. In such cases, the separate endpoint-specific presence views must be combined into a single one. The process is known as presence aggregation.

For example, consider the presence states of a user. The user is busy if the individual is talking on a mobile phone, even when her desk phone is free, her laptop computer is turned off, and her desktop computer is running and available. For other users, the individual is simply busy on the phone. Regardless of which phone the individual is using, the user is unlikely to answer calls. Presenting all the device-specific presence state can be confusing and even misleading. If a contact happens to focus on the state of the desk phone while overlooking the other endpoints, the contact would conclude incorrectly that the user is available for a chat. This is a scenario where the endpoint-specific presence states should be combined together to yield a single overall presence state for the user.

Microsoft Lync Server 2013 includes a predefined aggregation script. This aggregation script is specific to Microsoft Lync 2013. It applies the aggregation to the presence state, location, and the device capabilities of a presentity; obtains the input from Container 2 and 3; and then submits the resulting and aggregated [state category instance value elements](state-category-instance-value-elements.md) and [services category instance value element](services-category-instance-value-element.md) category instances to Container 100, 200, 300, or 400. When a [state category instance value elements](state-category-instance-value-elements.md) or [device category instance value element](device-category-instance-value-element.md) category instance is published or updated in Container 2 or 3, the aggregation script will be invoked. Lync 2013 relies on this aggregation script to publish aggregated presence state and presence capabilities. To interoperate with Lync 2013 or to leverage this default aggregation script in your application, you must have a clear understanding of the behaviors expected from Container 2 and 3. For more information, see [Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md).

If an application wishes to support application-specific custom aggregation, the application is responsible for implementing the corresponding aggregation script, which can be invoked on the client or in a middle-tier. To avoid potential interference with the predefined aggregation script, the application may need to avoid using the predefined Aggregation containers.

## See also

#### Concepts

[Programming with Enhanced Presence](programming-with-enhanced-presence.md)

