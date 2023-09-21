﻿---
title: UCMA 4.0 SDK software and hardware requirements
TOCTitle: Software and hardware requirements
ms:assetid: 521f7820-f6ed-4706-905d-9802674ab029
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465960(v=office.15)
ms:contentKeyID: 57102450
ms.date: 07/25/2014
mtps_version: v=office.15
---

# UCMA 4.0 SDK software and hardware requirements


**Applies to:** Lync 2013 | Lync Server 2013

This topic describes the software and hardware requirements for Microsoft Unified Communications Managed API 4.0 SDK.

## Software requirements

The following are the software requirements for a successful installation of UCMA 4.0 SDK.

  - Supported operating systems
    
      - Microsoft Windows Server 2008 R2 SP1 or higher service pack, 64-bit version
    
      - Microsoft Windows Server 2012
    
      - Microsoft Windows 7 SP1 or higher service pack, 64-bit (see following note)
    

    > [!IMPORTANT]
    > <UL>
    > <LI>
    > <P>UCMA 4.0 SDK is available only in a 64-bit version.</P>
    > <LI>
    > <P>Windows XP and Windows Server 2008 are not supported.</P>
    > <LI>
    > <P>Development is supported only in 64-bit environments.</P>
    > <LI>
    > <P>The Desktop Experience feature must be enabled on Windows Server 2008 R2 SP1. For more information, see <A href="http://technet.microsoft.com/library/cc772567.aspx">Desktop Experience Overview</A>.</P>
    > <LI>
    > <P>Media Foundation is required on Windows Server 2012.</P></LI></UL>



  - Microsoft Windows PowerShell 3.0 RTM
    

    > [!IMPORTANT]
    > <P>To install PowerShell 3.0, see <A href="http://www.microsoft.com/download/details.aspx?id=34595">Windows Management Framework 3.0</A>.</P>



  - Microsoft .NET Framework 4.5

**Notes**

  - Side-by-side installations of UCMA 4.0 SDK and Microsoft Unified Communications Managed API (UCMA) 3.0 SDK are not supported.

  - When Windows Media format is installed or enabled, the computer must be restarted.
    
    Windows Media Format must be present if you use UCMA 4.0 to develop applications that play or record media.

  - UcmaSdkSetup.exe must be run with elevated privileges.

## Hardware requirements

The following are the hardware requirements for successful installation of UCMA 4.0 SDK.

  - Typical current hardware configurations with a minimum of 2 GB of RAM are recommended for the supported operating systems.

