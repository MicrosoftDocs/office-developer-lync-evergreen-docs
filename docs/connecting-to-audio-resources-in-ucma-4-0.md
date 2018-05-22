---
title: Connecting to audio resources in UCMA 4.0
TOCTitle: Connecting to audio resources in UCMA 4.0
ms:assetid: 8da6dc06-69b0-4e7c-b42e-1011cad4223f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466126(v=office.15)
ms:contentKeyID: 57103419
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Connecting to audio resources in UCMA 4.0


_**Applies to:** Lync 2013 | Lync Server 2013_

A hosting .NET application uses the **SetAudioVideoCall()** method to bind an instance of the [Browser](https://msdn.microsoft.com/en-us/library/gg452712\(v=office.15\)) with an [AudioVideoCall](https://msdn.microsoft.com/en-us/library/hh383901\(v=office.15\)) object.

An [AudioVideoCall](https://msdn.microsoft.com/en-us/library/hh383901\(v=office.15\)) object contains an instance of [AudioVideoFlow](https://msdn.microsoft.com/en-us/library/hh383533\(v=office.15\)), which includes the audio devices in Microsoft Unified Communications Managed API 4.0 that will be used to record audio, play audio, send and receive telephone keypad tones, and connect to speech engines that convert spoken utterances into text and convert text into synthesized speech during the processing of a call. For more information about the audio devices in UCMA 4.0, see [AudioVideoFlow](https://msdn.microsoft.com/en-us/library/hh383533\(v=office.15\)).

The .NET application must ensure that the call is established and is active prior to calling **SetAudioVideoCall()**. After the call to the **SetAudioVideoCall** method has been made, the .Net application can launch the [Browser](https://msdn.microsoft.com/en-us/library/gg452712\(v=office.15\)).

