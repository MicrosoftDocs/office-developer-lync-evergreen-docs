﻿---
title: Calls
TOCTitle: Calls
ms:assetid: 010a8697-bd7a-47db-aeb5-183392f0cb1f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465990(v=office.15)
ms:contentKeyID: 57102808
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Calls


**Applies to:** Lync 2013 | Lync Server 2013

A call is a communication session between two endpoints: a local endpoint and a remote endpoint. UCMA 4.0 represents the call concept by the [Call](https://msdn.microsoft.com/library/hh384235\(v=office.15\)) abstract class, and provides non-abstract classes that implement three specific types of calls:

  - [InstantMessagingCall](https://msdn.microsoft.com/library/hh161841\(v=office.15\)) class.
    
    An **InstantMessagingCall** instance is used in a communication session for which the media type is Message, or text.

  - [AudioVideoCall](https://msdn.microsoft.com/library/hh383901\(v=office.15\)) class.
    
    An **AudioVideoCall** instance is used in a communication session for which the media type is Audio.
    

    > [!IMPORTANT]
    > <P>The default media provider for the <STRONG>AudioVideoCall</STRONG> class does not support the Video media type.</P>



  - [BackToBackCall](https://msdn.microsoft.com/library/hh365598\(v=office.15\)) class.
    
    A **BackToBackCall** instance represents a logical SIP network element that mediates SIP signaling between two call legs. A **BackToBackCall** instance can be used to connect two clients that send and receive audio alone or audio and video.

This section describes common operations that a UCMA-based application performs on calls.

## In this section

  - [Call state transitions](call-state-transitions.md)

  - [Registering for call events](registering-for-call-events.md)

  - [Impersonating a user](impersonating-a-user.md)

  - [Adding an instant messaging or audio/video call](adding-an-instant-messaging-or-audio-video-call.md)

  - [Establishing an outgoing call](establishing-an-outgoing-call.md)

  - [Accepting an incoming call](accepting-an-incoming-call.md)

  - [Transferring a call](transferring-a-call.md)

  - [Call park](call-park.md)

  - [Back-to-back user agent](back-to-back-user-agent.md)

