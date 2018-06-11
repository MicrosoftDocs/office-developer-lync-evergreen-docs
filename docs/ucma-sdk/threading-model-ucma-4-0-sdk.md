---
title: Threading model (UCMA 4.0 SDK)
TOCTitle: Threading model
ms:assetid: abdf2e3d-c235-4ff9-b8b0-9b709e7b22f8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466080(v=office.15)
ms:contentKeyID: 57103186
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Threading model (UCMA 4.0 SDK)


**Applies to:** Lync 2013 | Lync Server 2013

Microsoft Unified Communications Managed API 4.0 is designed be multi-thread safe. Some objects that are used to configure settings or options or that are used to contain data passed into an API are exceptions.

  - An application can invoke methods from different threads. In addition, the platform can be performing work as a result from interacting with remote applications. The application should be prepared to handle exceptions as described in [Platform behaviors (methods and properties)](platform-behaviors-methods-and-properties.md).

  - UCMA 4.0 will raise events and invoke method callbacks using worker threads. If an application throws an exception in one of the event handlers or callback methods, the worker thread can crash unless the application registers for handling unhandled exceptions. For more information, see [UCMA 4.0 exception model](ucma-4-0-exception-model.md).

  - When an operation is invoked on an object that is already terminated, the callback associated with that operation can be invoked in the application thread itself. When this happens, the **CompletedSynchronously** property is set to true. For more information about **CompletedSynchronously**, see [IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455).

  - The application thread will not be used by UCMA 4.0 to perform internal operations that take a long time.

