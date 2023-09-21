---
title: Starting a media flow
TOCTitle: Starting a media flow
ms:assetid: 8ee8b023-5093-44a5-b22a-cff207d5e5ac
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466034(v=office.15)
ms:contentKeyID: 57103027
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Starting a media flow


**Applies to:** Lync 2013 | Lync Server 2013

The media flow for a call provides the media that an application consumes.

When an application establishes a call, the platform creates an appropriately-typed media flow, using a media provider of the appropriate type. For example, establishing an audio/video call triggers the platform to use an internal audio/video media provider to create an [AudioVideoFlow](https://msdn.microsoft.com/library/hh383533\(v=office.15\)) object for the call.

Applications can register for state changes in the media flow instance that is associated with a call (for example, an audio/video call’s **AudioVideoFlow** object). The basic states of a media flow object are exposed through its [State](https://msdn.microsoft.com/library/hh349893\(v=office.15\)) property and are Idle, Active, and Terminated. When the media flow state is **Active**, the application can send or receive media. For example, for an audio/video call, the application can use all of the capabilities of a [Player](https://msdn.microsoft.com/library/hh383679\(v=office.15\)) or [Recorder](https://msdn.microsoft.com/library/hh382678\(v=office.15\)). For an instant message call, the application can start sending messages.

Applications can also configure the media flow to the extent that the flow is exposed in the flow object.

