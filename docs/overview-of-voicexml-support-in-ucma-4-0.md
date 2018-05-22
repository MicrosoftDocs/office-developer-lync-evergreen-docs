---
title: Overview of VoiceXML support in UCMA 4.0
TOCTitle: Overview of VoiceXML support in UCMA 4.0
ms:assetid: 309069f8-2e0b-4afb-99b8-bae39aa1d53b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466120(v=office.15)
ms:contentKeyID: 57103413
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Overview of VoiceXML support in UCMA 4.0


_**Applies to:** Lync 2013 | Lync Server 2013_

VoiceXML support in the Microsoft Unified Communications Managed API 4.0 consists of a VoiceXML runtime and the .NET namespace [Microsoft.Rtc.Collaboration.AudioVideo.VoiceXml](https://msdn.microsoft.com/en-us/library/gg452705\(v=office.15\)).

The namespace consists of the [Browser](https://msdn.microsoft.com/en-us/library/gg452712\(v=office.15\)) class, which provides access to the VoiceXML runtime and to the telephony and audio functionality in UCMA 4.0. This functionality facilitates automated communication with callers.


> [!NOTE]
> <P><A href="https://msdn.microsoft.com/en-us/library/gg452712(v=office.15)">Browser</A> derives from the <STRONG>Browser</STRONG> class in the <STRONG>Microsoft.Speech.VoiceXml</STRONG> namespace.</P>



To run a VoiceXML application in UCMA 4.0, you must create a .NET application. Your .NET application answers calls, launches a **Browser** for the VoiceXML session, and responds to **Browser** events. See [Tasks of the host .NET application](tasks-of-the-host-net-application.md) for more information.

Also, your .NET application can track how the VoiceXML interpreter executes elements in VoiceXML documents. You can use the event-driven feedback from VoiceXML processing to identify problem areas or inefficiencies in VoiceXML documents, and to tune the performance of VoiceXML applications. See [Browser Class (Microsoft.Speech)](https://msdn.microsoft.com/en-us/library/hh378332\(v=office.15\)) for more information about the events that a **Browser** instance generates during a VoiceXML session.

### VoiceXML runtime

The VoiceXML runtime includes a VoiceXML interpreter that processes the elements in VoiceXML documents. The VoiceXML interpreter processes elements that control dialog flow, including variables, events, and executable elements. Other VoiceXML elements specify parameters such as timeouts and other settings that govern resource fetching.

The VoiceXML interpreter also processes speech recognition grammars and speech synthesis prompts that are included inline or linked externally from the VoiceXML document. Grammars define which words the application will recognize in VoiceXML dialogs, while speech synthesis prompts contain the text that the application will speak. The VoiceXML interpreter may also instruct the Browser to access and play back to the caller pre-recorded audio files instead of synthesized speech.

### Browser

The **Browser** acquires the documents for the VoiceXML runtime to process, and carries out instructions from the VoiceXML interpreter to communicate with a caller.

To communicate with a caller, the **Browser** connects to audio functionality in UCMA 4.0, such as speech recognition, Dual-Tone Multi-Frequency (DTMF) tone recognition, audio recording, speech synthesis, and audio playback.

While processing the elements in VoiceXML documents, the **Browser** generates events that inform the hosting .NET application about the status of the call.

## Creating VoiceXML applications

The Unified Communications Managed API (UCMA) 4.0 documentation does not instruct developers on creating VoiceXML applications. See the [VoiceXML Tutorial](http://msdnstage.redmond.corp.microsoft.com/en-us/library/ff770014.aspx) on MSDN for instructions and examples that will introduce you to VoiceXML authoring.

Additional resources include the following specifications of the World Wide Web Consortium (W3C):

  - [Voice Extensible Markup Language (VoiceXML) Version 2.0](http://www.w3.org/tr/2004/rec-voicexml20-20040316/)

