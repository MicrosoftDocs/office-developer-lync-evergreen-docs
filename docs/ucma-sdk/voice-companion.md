﻿---
title: Voice companion
TOCTitle: Voice companion
ms:assetid: 088fd5e6-bd3b-41d7-8675-07ba89833cea
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465940(v=office.15)
ms:contentKeyID: 57102435
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Voice companion


**Applies to:** Lync 2013 | Lync Server 2013
 

UCMA enables collaboration from anywhere and from any device, even a simple PSTN phone.

A Voice Companion is intended to enable the user to dial in from a phone, authenticate easily using a PIN, and access all of his or her Exchange Server- and Microsoft Lync Server 2013-related information and content: read mail using text-to-speech (TTS), send short, default replies using speech recognition and DTMF, and leverage the contact list and presence concepts of Lync Server 2013 in a voice UI.

The following illustration shows the components involved in a voice companion application.

![Personal virtual assistant details](images/Dn465940.UCMA-PVA2(Office.15).jpg "Personal virtual assistant details")

Other names for the Voice Companion scenario include Personal Virtual Assistant, Auto Assistant, and Voice Access.


### Features enabled by UCMA

  - Personal identification number-based authentication and support for alternative authentication.

  - In-conference and conversation virtual assistance using DTMF or speech recognition.
    
    The services offered for voice or DTMF include:
    
      - Presence, contacts, and groups.
    
      - Outbound alerts and notifications, such as "Dial me when the meeting begins."

## Typical call flow usage

The general call flow typical of the voice companion application is as follows:

1.  A new incoming call arrives at the UCMA application from the phone user, by way of the Mediation server.

2.  The UCMA application asks the user to supply a personal identification number (PIN), and authenticates that PIN against the Lync Server 2013 PIN for that user (or other PIN validation source).

3.  The UCMA application plays recorded or TTS prompts and performs recognition of speech or DTMF against the responses, allowing for voice-UI access to Microsoft Lync 2013 features, such as presence and contacts.

4.  The UCMA application then takes action on behalf of that user, connecting him or her by means of a back-to-back user agent with people in the contact list or the Contact Store.

5.  UCMA can then serve as a virtual conference assistant, intercepting user commands entered as DTMF or (optionally) speech, so that the user can control the conference.

6.  (Using or later Exchange versions) A user can use the application to read e-mail, and the application can inform the user of upcoming meetings, or automatically dial out to another user before a meeting starts.

## Related features

UCMA-based IVR applications include the full power of Microsoft.Speech-based speech recognition, text-to-speech, and DTMF handling. A user can call a UCMA application, be connected to a custom IVR (which can be VoiceXML-based), provide his or her information to the IVR, and then be connected to streaming music-on-hold. Meanwhile, the information that the user provides is passed to the application, allowing the application to intelligently route the call, fetch information from external sources, and play customized messages to the user.

  - The [Player](https://msdn.microsoft.com/library/hh349780\(v=office.15\)), [Recorder](https://msdn.microsoft.com/library/hh381624\(v=office.15\)), and [ToneController](https://msdn.microsoft.com/library/hh349643\(v=office.15\)) classes can be used to implement an IVR workflow that involves playing prerecorded prompts, handling DTMF tones, and recording audio.

  - The [Browser](https://msdn.microsoft.com/library/gg452712\(v=office.15\)) class can interpret VoiceXML code to implement workflow logic that involves TTS or speech recognition.

  - The Connector objects (the [SpeechRecognitionConnector](https://msdn.microsoft.com/library/hh383253\(v=office.15\)) and [SpeechSynthesisConnector](https://msdn.microsoft.com/library/hh349773\(v=office.15\)) classes) can be used to implement an application that involves TTS or speech recognition.

  - Recording and Music on Hold
    
    UCMA applications can play audio content to the caller on demand, record the audio portion of a call, and play music-on-hold to users while waiting for the IVR to perform background tasks.

Additional features are as follows:

  - PIN-based Authentication and Alternative Authentication
    
    UCMA applications can authenticate a user to the Lync Server 2013/Exchange servers by means of an Lync Server 2013 user PIN, or by authenticating a user separately, and then using server trust to take actions on that user’s behalf.

  - User Alerts and Dial-out at Conference Time
    
    A UCMA application can become aware of conferences (through Exchange) and dial out to a user automatically at the scheduled time, reducing the need to remember conference IDs when on the road. UCMA applications can also be set to take actions at a later time, notifying a user when his conference targets are available, and connecting them automatically.

  - Presence and Contacts and Groups
    
    UCMA applications can get and set a user’s presence on behalf of that user, as well as access a user’s contact list and the Lync Server 2013 Contact Store, and then surface that information to the user through custom user interfaces.

  - Recording and Playback
    
    UCMA applications can record the audio portion of a call, play audio content to the caller on demand, and play pre-recorded prompts as part of an IVR/voice user interface.

