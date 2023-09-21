﻿---
title: Sending and receiving page-mode messages
TOCTitle: Sending and receiving page-mode messages
ms:assetid: f6aadb54-8b83-418f-bc82-ed36187ea561
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466063(v=office.15)
ms:contentKeyID: 57103056
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Sending and receiving page-mode messages


**Applies to:** Lync 2013 | Lync Server 2013

An application can begin sending messages in page mode after a [RealTimeEndpoint](https://msdn.microsoft.com/library/hh366081\(v=office.15\)) instance is created and registered, provided that the endpoint is an instance of the [SipEndpoint](https://msdn.microsoft.com/library/hh348350\(v=office.15\)) class. The application on the sending side can send a message synchronously (using [SendMessage()](https://msdn.microsoft.com/library/hh350225\(v=office.15\))) or asynchronously (using [BeginSendMessage()](https://msdn.microsoft.com/library/hh349151\(v=office.15\)) and [EndSendMessage(IAsyncResult)](https://msdn.microsoft.com/library/hh382471\(v=office.15\)). Page-mode messages are delivered only when the recipient endpoint is online and has subscribed to the [MessageReceived](https://msdn.microsoft.com/library/hh350010\(v=office.15\)) event.

The topics in this section describe how to send page-mode messages synchronously and asynchronously, and how to receive page-mode messages.

  - [Sending page-mode messages synchronously](sending-page-mode-messages-synchronously.md)

  - [Sending page-mode messages asynchronously](sending-page-mode-messages-asynchronously.md)

  - [Receiving page-mode messages](receiving-page-mode-messages.md)

