---
title: Migrate applications to Lync Server 2013 SDK
TOCTitle: Migrate applications to Lync Server 2013 SDK
ms:assetid: 5e311480-1ab4-4a2a-88a8-c7f5015494e8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439061(v=office.15)
ms:contentKeyID: 57096217
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Migrate applications to Lync Server 2013 SDK

Learn how to migrate applications to run on a Microsoft Lync Server 2013 computer.


_**Applies to:** Lync Server 2013_

To migrate applications that were developed by using Microsoft Live Communications Server SDK, Microsoft Office Communications Server 2007, or Microsoft Office Communications Server 2007 R2 SDK to run on Microsoft Lync Server 2013, you must recompile the applications by using the 64-bit version of the Microsoft Lync Server 2013 SDK.

Managed code applications must be compiled by using the Microsoft .NET Framework 2.0 and later versions of the .NET Framework. Microsoft SIP Processing Language (MSPL) applications must be verified by using the SPL Compiler (CompileSPL.exe).

All applications that were built to run on Office Communications Server 2007 R2 will run on Lync Server 2013 with the following exceptions:

  - Microsoft SIP Processing Language (MSPL) applications that refer to the built-in constants of **UserOptions.PublicCloud**, **UserOptions.Federation**, **UserOptions.OutsideAccess**, and **UserOptions.RpAllowed** must be revised so they do not use these constants.

  - MSPL applications that invoke the **QueryUserPolicy** function must be revised to comply with the new function signature, which now excludes the **UserPolicyType** parameter.

  - MSPL applications that invoke the **RegistrarEndpoint** type must be revised so they do not use the **AllSupportForking**, **SupportsForking**, **HasPresence**, **Availability**, **Activity**, **AgeOfPresence**, and **PresenceDoc** properties, which are no longer supported.

In Lync Server 2013, the WMI-based Server Management API is no longer supported. To register, modify, or remove a SIP application, you must use Microsoft Windows PowerShell commands. For more information, see [How to: Register a SIP application](how-to-register-a-sip-application.md) and [How to: Manage a SIP application](how-to-manage-a-sip-application.md).

## See also

#### Concepts

[Get started with Lync Server 2013 SDK](get-started-with-lync-server-2013-sdk.md)

