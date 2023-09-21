﻿---
title: InstantMessagingFlow
TOCTitle: InstantMessagingFlow
ms:assetid: 5cb8451a-a295-4a0b-b6b5-391b27a6c485
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466025(v=office.15)
ms:contentKeyID: 57103018
ms.date: 07/25/2014
mtps_version: v=office.15
---

# InstantMessagingFlow


**Applies to:** Lync 2013 | Lync Server 2013

An [InstantMessagingFlow](https://msdn.microsoft.com/library/hh383312\(v=office.15\)) instance represents an instant messaging connection with a single remote participant.

The [ComposingTimeoutValue](https://msdn.microsoft.com/library/hh349262\(v=office.15\)) property is used to control the time-out value that reverts the local composing state to **Idle**. If an application sets [LocalComposingState](https://msdn.microsoft.com/library/hh350219\(v=office.15\)) to **Composing**, it's automatically reverted to **Idle** if the application does not set **LocalComposingState** to **Composing** again within this idle time-out. Several seconds can elapse after the time-out occurs for the state to change to **Idle**. An application cannot set **LocalComposingState** to **Idle**.

Getting or setting **LocalComposingState** will result in a "Typing" or "Idle" notification to be sent to remote participants. After being set to **Typing**, automatic refresh of the **Typing** state occurs every three seconds until a message is sent or the state is set explicitly to **Idle**. If a message is sent, it's not necessary to set the state to **Idle** because the composing state will be automatically reset to **Idle**. A [RemoteComposingStateChanged](https://msdn.microsoft.com/library/hh349462\(v=office.15\)) event will not be raised when this property is set to **Idle**.

An application uses the [Initialize(InstantMessagingFlowTemplate)](https://msdn.microsoft.com/library/hh382523\(v=office.15\)) method to configure an **InstantMessagingFlow** instance as **ConsumedLocally** (the default) or as **ProxiedToRemoteEntity**, values of the [InstantMessageConsumptionMode](https://msdn.microsoft.com/library/hh366078\(v=office.15\)) enumeration. If the flow is configured for **ProxiedToRemoteEntity**, an application must register for the [MessageReceived](https://msdn.microsoft.com/library/hh383170\(v=office.15\)) event and must send message delivery notifications using [BeginSendSuccessDeliveryNotification(InstantMessageId, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh366216\(v=office.15\)) or [BeginSendFailureDeliveryNotification(InstantMessageId, Int32, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh381150\(v=office.15\)) on each received message. Failure to send these delivery notification messages can result in a memory leak.

