﻿---
title: AudioVideoMcuSession
TOCTitle: AudioVideoMcuSession
ms:assetid: e22ada5b-ba71-4c0c-92dc-273c1b5ed185
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466029(v=office.15)
ms:contentKeyID: 57103022
ms.date: 07/25/2014
mtps_version: v=office.15
---

# AudioVideoMcuSession


**Applies to:** Lync 2013 | Lync Server 2013

The [AudioVideoMcuSession](https://msdn.microsoft.com/library/hh385298\(v=office.15\)) class represents the audio/video specific implementation of the media-agnostic [McuSession](https://msdn.microsoft.com/library/hh384975\(v=office.15\)) class. The class encapsulates operations and events relevant to the Audio-Video Multipoint Control Unit (MCU).

## AudioVideoMcuSession state transitions

The **AudioVideoMcuSession** state transitions are shown in the following illustration.

![InstantMessagingMcuSession state transitions](images/Dn466029.StateMach_McuSession(Office.15).jpg "InstantMessagingMcuSession state transitions")

1.  The transition from **Idle** to **Active** occurs after [ConferenceSession](https://msdn.microsoft.com/library/hh349315\(v=office.15\)) has joined a conference. An **AudioVideoMcuSession** instance can become active either before or after the callback passed to [BeginJoin](https://msdn.microsoft.com/library/hh349641\(v=office.15\)) is called, depending on when the MCU is activated on the server.

2.  The transition from **Idle** to **Terminated** occurs when the parent **ConferenceSession** object joins a conference that does not support the same MCU type (for example, when an attempt is made to join an IM-only conference to an **AudioVideoMcuSession** instance).

3.  The transition from **Active** to **Retrying** occurs when the Focus detects that the MCU is failing over. In this case, UCMA 4.0 terminates the call with that MCU, provided that the call already exists. This transition also occurs when the **ConferenceSession** object reconnects to the Focus Because the MCU is not known to be failing over, the call is not terminated in this case.

4.  The transition from **Retrying** to **Active** occurs when the failover process is complete, or when the **ConferenceSession** has reconnected to the Focus and the MCU is active. It's possible for the **ConferenceSession** to reconnect to the Focus but the **AudioVideoMcuSession** state does not change to **Active** if the MCU has not been activated on the server.

