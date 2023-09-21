﻿---
title: Standalone IVR application
TOCTitle: Standalone IVR application
ms:assetid: e824ca31-c9fa-4ba6-99de-bdc090e3547c
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465937(v=office.15)
ms:contentKeyID: 57102431
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Standalone IVR application


**Applies to:** Lync 2013 | Lync Server 2013

Microsoft Unified Communications Managed API 4.0 can be used to create an application that works directly against SIP-PSTN gateways (that are based on RFC 3261) and IP-PBXs to deliver a UCMA-only basic IVR application.

A UCMA-based IVR can communicate directly with SIP PSTN gateways and IP-PBXs, providing self-service capabilities with voice and DTMF input, such that a user can call an IVR, enter some information, and receive access to resources by way of DTMF input or TTS. Standalone IVR applications are practical for cases where users must be able to access information or receive notifications from anywhere and on any device.

The following illustration shows the components involved in a standalone IVR application.

![Standalone IVR details](images/Dn465937.UCMA-StandaloneIVR2(Office.15).jpg "Standalone IVR details")

Other names for the Standalone IVR scenario include voicemail, automated information bot, and self-help IVR.

## Typical call flow usage

The general call flow typical of a standalone interactive voice response (IVR) application is as follows:

1.  A new incoming call arrives at the UCMA application from an endpoint (such as Microsoft Lync 2013), SIP gateway, or IP-PBX.

2.  The UCMA application plays prompts (prerecorded media or text-to-speech (TTS)) and performs recognition against the DTMF or spoken responses, allowing for IVR traversal. The application can also record the call to a file.

3.  UCMA can then direct the call (using a back-to-back user agent) to an agent, and remain in the call path. For more information, see [Back-to-back user agent](back-to-back-user-agent.md).

## Related features

UCMA-based IVR applications include the full power of Microsoft.Speech-based speech recognition, text-to-speech, and DTMF handling. A user can call a UCMA application, be connected to a custom IVR (which can be VoiceXML-based), provide his or her information to the IVR, and then be connected to streaming music-on-hold. Meanwhile, the information that the user provides is passed to the application, allowing the application to intelligently route the call, fetch information from external sources, and play customized messages to the user.

  - The [Player](https://msdn.microsoft.com/library/hh349780\(v=office.15\)), [Recorder](https://msdn.microsoft.com/library/hh381624\(v=office.15\)), and [ToneController](https://msdn.microsoft.com/library/hh349643\(v=office.15\)) classes can be used to implement an IVR workflow that involves playing prerecorded prompts, handling DTMF tones, and recording audio.

  - The [Browser](https://msdn.microsoft.com/library/gg452712\(v=office.15\)) class can interpret VoiceXML code to implement workflow logic that involves TTS or speech recognition.

  - Connector objects (the [SpeechRecognitionConnector](https://msdn.microsoft.com/library/hh383253\(v=office.15\)) and [SpeechSynthesisConnector](https://msdn.microsoft.com/library/hh349773\(v=office.15\)) classes) can be used to implement an application that involves TTS or speech recognition.

  - Recording and Music on Hold
    
    UCMA applications can play audio content to the caller on demand, record the audio portion of a call, and play music-on-hold to users while waiting for the IVR to perform background tasks.

