---
title: Shutdown and termination
TOCTitle: Shutdown and termination
ms:assetid: 984533c3-4d46-408e-a958-ce1ed87eedd5
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466076(v=office.15)
ms:contentKeyID: 57103070
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Shutdown and termination


**Applies to:** Lync 2013 | Lync Server 2013

The following discusses general behavior when components in UCMA 4.0 are terminated, as well as behavior that is expected in applications written using UCMA 4.0:

  - When a component is terminated, it's responsible for terminating all contained subcomponents. For example, terminating the platform causes all endpoints to be terminated. Terminating an endpoint terminates all conversations. Terminating a conversation terminates all calls, conference sessions, media flows, and any pending conference invitations. Terminating a conference session terminates all MCU sessions.

  - Terminating a conversation may not result in the termination of components that serve the conversation but might be shared with other conversations. For example, a [Player](https://msdn.microsoft.com/library/hh349780\(v=office.15\)) will not be terminated when a conversation is terminated. It's the responsibility of the application to stop a **Player** (using the [Stop](https://msdn.microsoft.com/library/hh350156\(v=office.15\)) method on the **Player** class) and close all media sources that are being used, unless the application intends to continue using those resources at a later time.

  - A component will not complete a terminate operation until all contained components and pending operations are completed. The component is responsible for maintaining the pending operations to be terminated when the component is terminated.

  - **BeginTerminate** will not throw an exception unless it's passed an invalid argument. For example, the signaling headers collection passed may contain invalid or disallowed headers and an exception is thrown even before the operation can start.

  - It's permissable to call **BeginTerminate** multiple times. However, a second call to **BeginTerminate** while a previous call is pending will not complete until the component is actually terminated.

  - **BeginTerminate** on an object can complete synchronously if it's called after the object is already terminated.

