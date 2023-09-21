---
title: PSTN user authentication
TOCTitle: PSTN user authentication
ms:assetid: 8e0d8150-57bc-49ab-a190-e7e25d42df05
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465941(v=office.15)
ms:contentKeyID: 57102434
ms.date: 07/25/2014
mtps_version: v=office.15
---

# PSTN user authentication


**Applies to:** Lync 2013 | Lync Server 2013

Microsoft Unified Communications Managed API 4.0 applications add the ability to authenticate a user to the Microsoft Lync Server 2013/Exchange Server 2013 servers by means of a Lync Server 2013 user personal identification number (PIN), or by authenticating a user separately, and then using server trust to take actions on behalf of that user.

UCMA 4.0 includes the **ApplicationPinServices** class, which has a method that can be used to verify a PIN.

With the ability to authenticate users by PINs, a mobile user can call a UCMA 4.0 applications, present a single PIN, and then be authenticated to his or her Exchange 2013 mailbox to perform such tasks as reading mail using text-to-speech (TTS) or accessing his or her contact list. The Voice Companion sample that ships with Microsoft Unified Communications Managed API 4.0 SDK demonstrates how these actions can be carried out. For more information, see [Voice Companion (sample)](voice-companion-sample.md) and [Voice companion](voice-companion.md).

