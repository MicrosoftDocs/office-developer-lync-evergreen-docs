---
title: ToneController
TOCTitle: ToneController
ms:assetid: 10a21ab0-e63c-4c71-8ebc-5b57f6b3d523
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466039(v=office.15)
ms:contentKeyID: 57103032
ms.date: 07/25/2014
mtps_version: v=office.15
---

# ToneController


_**Applies to:** Lync 2013 | Lync Server 2013_

The [ToneController](https://msdn.microsoft.com/en-us/library/hh349643\(v=office.15\)) class is responsible for handling telephony tone communication between an [AudioVideoFlow](https://msdn.microsoft.com/en-us/library/hh383533\(v=office.15\)) instance and an application. A **ToneController** instance can send telephone keypad tones to or receive them from an attached **AudioVideoFlow** instance. Although **ToneController** and **AudioVideoFlow** instances operate independently of one other, communication is effective only when the attached **AudioVideoFlow** instance is in the **Active** state (that is, the **State** property on the **AudioVideoFlow** instance is **Active**).

An application can send a tone by calling one of the overloaded [Send](https://msdn.microsoft.com/en-us/library/hh366136\(v=office.15\)) methods, and provided that the attached **AudioVideoFlow** instance is in the **Active** state. If the **AudioVideoFlow** instance is in a state other than **Active** (that is, **Idle** or **Terminated**), an exception is not thrown.

An application can receive a tone if it has registered a handler for the [ToneReceived](https://msdn.microsoft.com/en-us/library/hh366378\(v=office.15\)) event.

An application can detect when a fax tone is received from a remote peer. An application that has subscribed to the [IncomingFaxDetected](https://msdn.microsoft.com/en-us/library/hh382433\(v=office.15\)) event on the [ToneController](https://msdn.microsoft.com/en-us/library/hh349643\(v=office.15\)) class can detect an incoming fax tone in either of the following situations:

  - In-band fax tone (CNG tone event in the RTP stream sent according to RFC 2833)

  - Out-of-band fax tone (CNG tone is sent over the RTP event)

  - The endpoint receives a SIP ReINVITE with a=image

