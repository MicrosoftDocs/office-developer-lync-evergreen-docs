---
title: TrustedConferenceParticipant (QuickStart)
TOCTitle: TrustedConferenceParticipant (QuickStart)
ms:assetid: 66642dc8-9204-4bc6-a69a-95e4380704f3
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454831(v=office.15)
ms:contentKeyID: 57103762
ms.date: 07/25/2014
mtps_version: v=office.15
---

# TrustedConferenceParticipant (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013



Sample name: TrustedConferenceParticipant

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\TrustedConferenceParticipant

## Description

The application establishes an application endpoint and impersonates a user who creates and joins an *ad hoc* conference. The application endpoint then joins the conference as a trusted participant. The trusted participant then monitors the roster of the MCU for the conference. When a new participant is detected, a new audio-video call is created. This audio-video call is then configured to route DTMF from the new participant to the application and audio from the application to the participant. The application can also send an invitation to a specified user to show how the impersonated and trusted joins are surfaced. For more information about provisioning trusted applications and endpoints in Microsoft Lync Server 2013, see [Activating a UCMA 4.0 trusted application](activating-a-ucma-4-0-trusted-application.md), [General application activation](general-application-activation.md), and [Activating a manually-provisioned application](activating-a-manually-provisioned-application.md).

## Features

- *Ad hoc* conference creation

- Conversation impersonation

- Joining a conference as a trusted participant (the trusted participant’s endpoint will not be visible in the roster)

- Configuration of audio-video call routes

## Prerequisites

- Microsoft Lync Server 2013.

- Provisioned trusted [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)) object

- A currently logged-on client on Lync Server 2013.

## Running the sample

1.  The configuration settings in the accompanying App.config file are used by the sample. You will be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

3.  When the conference is established the sample will prompt for URIs to send invitations to the conference. (Pressing **ENTER** when prompted will skip this step.) This URI should be for a user who is currently signed into Microsoft Lync 2013. This user can join the conference to observe how other participants are presented and see that the entered DTMF or the response audio is not heard by the other participants of the conference.

