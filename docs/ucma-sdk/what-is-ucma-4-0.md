---
title: What is UCMA 4.0
TOCTitle: What is UCMA 4.0
ms:assetid: ebbfeb40-02ad-4045-bf46-b073406a5c26
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465943(v=office.15)
ms:contentKeyID: 57102437
ms.date: 07/25/2014
mtps_version: v=office.15
---

# What is UCMA 4.0


**Applies to:** Lync 2013 | Lync Server 2013

Microsoft Unified Communications Managed API 4.0 is used primarily to build middle-tier applications that work with Microsoft Lync Server 2013.

UCMA 4.0 provides a flexible managed-code platform for unified communication and collaboration that allows developers to implement communication-enabled and collaboration-enabled services against Lync Server 2013.

## UCMA 4.0 features

  - The platform contains a managed code endpoint API that is based on Session Initiation Protocol (SIP), and is written in Visual C\#.

  - The platform is multilayered, with different levels of abstraction, as shown in the following illustration. The components that make up the platform are shown in the blue blocks.
    
      - Unified Communications and Collaboration protocol layer (UCMA 4.0). The classes in this layer are exposed in the [Microsoft.Rtc.Collaboration](https://msdn.microsoft.com/library/hh384297\(v=office.15\)) namespace. The protocols include Enhanced Presence, Centralized Conference Control Protocol (C3P), Contacts and Groups, and Call Control.
        
        The **Microsoft.Speech** namespace can be used to provide speech recognition and speech synthesis capabilities in UCMA 4.0 applications.
        
        Interactive Voice Response (IVR) applications that can optionally use Voice XML can be created from classes contained in the [Microsoft.Rtc.Collaboration.AudioVideo.VoiceXml](https://msdn.microsoft.com/library/gg452705\(v=office.15\)) and **Microsoft.Speech.VoiceXml** namespaces (Microsoft.Rtc.Collaboration.AudioVideo.VoiceXml.dll and Microsoft.Speech.VoiceXml.dll, respectively). For more information, see [VoiceXML support in UCMA 4.0](voicexml-support-in-ucma-4-0.md).
    
      - Signaling layer. This layer provides access to the SIP/SIMPLE infrastructure. The classes in this layer are exposed in the [Microsoft.Rtc.Signaling](https://msdn.microsoft.com/library/hh365949\(v=office.15\)) namespace.
        
        The Audio stack is used by some classes in UCMA 4.0, but does not expose any public classes.
    

    > [!NOTE]
    > <P>UCMA 4.0 is contained in a single assembly, Microsoft.Rtc.Collaboration.dll.</P>

    
    ![Platform abstraction layers](images/Dn465943.UCMAOverallArch(Office.15).jpg "Platform abstraction layers")

  - The platform is highly scalable.
    
    The platform is able to support thousands of endpoints and concurrent communications and collaborations. The platform is designed for server operating systems (the recommended operating systems are Microsoft Windows Server 2008 SP2 64-bit or Windows Server 2008 R2), and is multi-threaded.

  - The platform provides high availability.
    
    The deployment model permits multiple, load-balanced application instances that allow for server-grade load balancing and fail-over. Dialog resiliency is built in to update the route set in the event of intermediate hop failures.

  - The platform is extensible.
    
    New modalities can be added to the existing communication framework, and extension headers and URI parameters can be supplied and consumed through the APIs.

