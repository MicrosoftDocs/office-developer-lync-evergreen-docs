---
title: High CPU usage and .NET thread pool
TOCTitle: High CPU usage and .NET thread pool
ms:assetid: 69540919-1351-4568-912e-ab535a93d9b1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466094(v=office.15)
ms:contentKeyID: 57103190
ms.date: 07/25/2014
mtps_version: v=office.15
---

# High CPU usage and .NET thread pool


_**Applies to:** Lync 2013 | Lync Server 2013_

If you experience unusually high CPU usage or an increase of CPU usage over time, it may be related to a known issue in the common language runtime (CLR) thread pool in .NET Framework 3.5 SP1.

## Determine whether your application is affected

Profile the application to find where the process time is spent. If significant time is spent in lock contention methods inside the CLR thread pool, you are likely affected by this issue.

Alternatively, connect the debugger to the process (or load a dump of the process into the debugger) and run the \!threadpool command from the sos.dll extension DLL. If the queue length is very low (0, 1, or 2), but the total number of worker threads is equal to or very close to Max Limit of worker threads, your application is very likely affected by this issue.

## Resolution

Limit the maximum number of worker threads in the thread pool by calling **ThreadPool**.**SetMaxThreads**. The number used should reflect the application's needs, and can vary from application to application.

