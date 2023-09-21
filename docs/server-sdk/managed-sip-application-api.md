---
title: Managed SIP Application API
TOCTitle: Managed SIP Application API
ms:assetid: 9e04a0e2-3b43-4114-acd9-71d64dc4fc2f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439068(v=office.15)
ms:contentKeyID: 57096227
ms.date: 02/11/2016
mtps_version: v=office.15
description: Explore Microsoft Lync Server 2013 SDK managed SIP applications. Learn about application manifests, MSPL scripts, .NET Framework applications, and more.
---

# Managed SIP Application API

Learn about Microsoft Lync Server 2013 SDK managed SIP applications.


**Applies to:** Lync 2013 | Lync Server 2013

A managed SIP application in a Microsoft Lync Server 2013 scenario includes an application manifest, a Microsoft SIP Processing Language (MSPL) script, and a .NET Framework application that uses at least the [Microsoft.Rtc.Sip](https://msdn.microsoft.com/library/jj266253\(v=office.15\)) namespace. The application manifest is used to specify message types to be processed by the managed SIP application. The MSPL script is used to dispatch the to-be-processed SIP messages to the managed message handler.

Managed SIP application, instead of a script-only message filter, development scenarios include:

  - Secure proxy applications that specifically authenticate and validate users, or perform additional encryption of specific message data.

  - Applications that can reference other external sources of information, besides the registrar, to determine proxy behavior. For example, a local database or Active Directory.

The basic classes for a managed SIP application include the [ServerAgent](https://msdn.microsoft.com/library/jj266157\(v=office.15\)) type and the base [Transaction](https://msdn.microsoft.com/library/jj265742\(v=office.15\)) type (which has two specific child types: [ServerTransaction](https://msdn.microsoft.com/library/jj265462\(v=office.15\)) and [ClientTransaction](https://msdn.microsoft.com/library/jj265716\(v=office.15\))). The **ServerAgent** object is the interface between the application and the Lync Server 2013 computer. The [Transaction](https://msdn.microsoft.com/library/jj265742\(v=office.15\)) objects are the managed code encapsulation of the [Transaction](https://msdn.microsoft.com/library/hh347122\(v=office.15\)) class that is exposed in the MSPL built-in functions. To improve efficiency, the lifetimes of [Transaction](https://msdn.microsoft.com/library/jj265742\(v=office.15\)) objects can be managed programmatically within the application.

The [Microsoft.Rtc.Sip](https://msdn.microsoft.com/library/jj266253\(v=office.15\)) namespace also supports two kinds of proxy applications:

  - [SIP Forwarding Proxy Application](managed-sip-application-as-forwarding-proxy.md)

  - [SIP Forking Proxy Application](managed-sip-application-as-forking-proxy.md)


> [!NOTE]
> <P>In Lync Server 2013, all server API applications must be compiled with the 64-bit version of Lync Server 2013 SDK.</P>



## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

