---
title: Page-mode messaging
TOCTitle: Page-mode messaging
ms:assetid: c05a6e23-3fb2-4d4b-a48e-eaeb576fdeff
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466059(v=office.15)
ms:contentKeyID: 57103052
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Page-mode messaging


**Applies to:** Lync 2013 | Lync Server 2013

In UCMA 4.0, an endpoint can send messages to another endpoint without establishing a signaling session. An operation of this type is referred to as *page-mode messaging*. In page mode, a message is delivered from the source to the target without a handshake being required between the two endpoints. UCMA 4.0 exposes the [SendMessage()](https://msdn.microsoft.com/library/hh350225\(v=office.15\)) overloaded methods for sending a page-mode message synchronously, and the [BeginSendMessage()](https://msdn.microsoft.com/library/hh349151\(v=office.15\)) overloaded methods and the [EndSendMessage(IAsyncResult)](https://msdn.microsoft.com/library/hh382471\(v=office.15\)) method for sending a page-mode message asynchronously.

The recipient of a page-mode message must subscribe to the [MessageReceived](https://msdn.microsoft.com/library/hh350010\(v=office.15\)) event in order to receive this type of message.

For more information, see [Sending and receiving page-mode messages](sending-and-receiving-page-mode-messages.md).

