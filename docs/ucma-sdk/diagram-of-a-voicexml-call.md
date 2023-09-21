﻿---
title: Diagram of a VoiceXML call
TOCTitle: Diagram of a VoiceXML call
ms:assetid: 81874951-9055-4c44-9869-fc2028ac957f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466124(v=office.15)
ms:contentKeyID: 57103417
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Diagram of a VoiceXML call


**Applies to:** Lync 2013 | Lync Server 2013

The following diagram shows a simplified representation of a VoiceXML call in Microsoft Unified Communications Managed API 4.0.

![Call to a VoiceXML-Based IVR Application](images/Dn466124.VoiceXMLCall_UCMA3(Office.15).jpg "Call to a VoiceXML-Based IVR Application")

1.  A person begins the call by entering the number for a service that they access by phone, for example a bank.

2.  The call arrives at a SIP server, such as Microsoft Lync Server 2013.

3.  The number is associated with a Microsoft Unified Communications Managed API 4.0 Endpoint, and the call is directed to this endpoint.

4.  The hosting .NET application listens for calls at the UCMA 4.0 endpoint, and takes calls as they arrive.

5.  When the .NET application takes a call, it launches an instance of the [Browser](https://msdn.microsoft.com/library/gg452712\(v=office.15\)). The application launches a separate **Browser** instance for each call that it answers.

6.  The **Browser** connects to audio devices in the UCMA 4.0 endpoint that allow the **Browser** to present audio to the caller or collect audio from the caller as instructed by the VoiceXML application.

7.  The VoiceXML Interpreter in the **Browser** processes the markup language in the VoiceXML application. The VoiceXML application may be on a web server, or may be hosted within UCMA 4.0.

8.  The **Browser** communicates with the caller as instructed by the VoiceXML application. To present information to the caller, the **Browser** plays recorded audio files or verbalizes synthesized speech. To collect information from the caller, the **Browser** recognizes or records the caller's speech or keypad touch tones. The VoiceXML application cannot communicate directly with the caller.

