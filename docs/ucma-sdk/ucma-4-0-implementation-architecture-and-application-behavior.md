---
title: UCMA 4.0 implementation architecture and application behavior
TOCTitle: UCMA 4.0 implementation architecture and application behavior
ms:assetid: 583aba66-4638-4158-b8fd-e22619d89dad
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466075(v=office.15)
ms:contentKeyID: 57103069
ms.date: 07/25/2014
mtps_version: v=office.15
---

# UCMA 4.0 implementation architecture and application behavior


**Applies to:** Lync 2013 | Lync Server 2013

This section is intended for application developers who use Microsoft Unified Communications Managed API 4.0, and discusses general platform behavior that is expected across various components. The topics in this section discuss guidelines that developers can use to properly create application code and identify code defects when correct behavior is not observed. These guidelines have been followed in the development of UCMA 4.0, with the goal of improving the quality of the platform by ensuring a consistent behavior across various components. These guidelines are also intended to make it easier for an application developer to implement the desired functionality, knowing that the platform guarantees a specific set of behaviors.

UCMA 4.0 exposes a variety of concepts in the API, such as platform, endpoint, conversation, call, conference session, MCU session, and media flow. All of these components expose asynchronous methods and events. An application can invoke these methods and register for the events that are raised. UCMA 4.0 uses thread-pool worker threads to make callbacks or to raise events. Typically, queues are used for raising events and for method completion callbacks. The topics in this section discuss issues for which the application can expect certain intended behavior. Some issues are discussed in more than one of the following topics, under different categories. This is done explicitly to make them easier to find.


> [!NOTE]
> <P>These behaviors apply only to UCMA 4.0 and may not be honored by the underlying signaling layer. The signaling layer is also accessible to an application that uses UCMA 4.0.</P>



## In This Section

  - [Asynchronous pattern](asynchronous-pattern.md)

  - [Threading model (UCMA 4.0 SDK)](threading-model-ucma-4-0-sdk.md)

  - [Queue usage model](queue-usage-model.md)

  - [Platform behaviors (methods and properties)](platform-behaviors-methods-and-properties.md)

  - [Shutdown and termination](shutdown-and-termination.md)

  - [Application behavior](application-behavior.md)

