﻿---
title: Registering for call events
TOCTitle: Registering for call events
ms:assetid: 444e43e5-516e-4043-a9b7-0646d2591995
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466010(v=office.15)
ms:contentKeyID: 57102988
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Registering for call events


**Applies to:** Lync 2013 | Lync Server 2013

Calls expose several events that can be useful to an application. For example, the [StateChanged](https://msdn.microsoft.com/library/hh365987\(v=office.15\)) event is raised when the state of the call changes and the [ConversationChanged](https://msdn.microsoft.com/library/hh384752\(v=office.15\)) event is raised when a call is moved to a new conversation is derived from the current conversation. A call will be moved to a derived conversation either when the remote participant of the call is different from the conversation’s remote participant or when the escalation operation fails to escalate all the established calls in the conversation. In the latter case, the calls for which the escalation operation failed will be moved to a derived conversation. Applications can use [Reason](https://msdn.microsoft.com/library/hh348459\(v=office.15\)) to determine why the call was moved to a derived conversation.

Applications must register for any events of interest before a call is established.

The following code demonstrates registering an event handler for the **StateChanged** event on an instant messaging call and implementing a simple event handler for this event.

```csharp
imCall.StateChanged += IMCall_StateChanged;
private void IMCall_StateChanged(object sender, CallStateChangedEventArgs<CallState> e)
{
}
```

The following code demonstrates registering an event handler for the **StateChanged** event on an audio/video call and implementing a simple event handler for this event.

```csharp
avCall.StateChanged += AVCall_StateChanged;
private void AVCall_StateChanged(object sender, CallStateChangedEventArgs<CallState> e)
{
  // Code for handling the StateChanged event.
}
```

