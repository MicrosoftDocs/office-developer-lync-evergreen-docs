---
title: Channel.ActionAvailabilityChanged event (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: ActionAvailabilityChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.AudioVideo.Channel.ActionAvailabilityChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.channel.actionavailabilitychanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601942
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.Channel.ActionAvailabilityChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Channel.ActionAvailabilityChanged event

Raised when the availability of a channel action changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ActionAvailabilityChanged As EventHandler(Of ChannelActionAvailabilityEventArgs)
'Usage
Dim instance As Channel
Dim handler As EventHandler(Of ChannelActionAvailabilityEventArgs)

AddHandler instance.ActionAvailabilityChanged, handler
```

``` csharp
public event EventHandler<ChannelActionAvailabilityEventArgs> ActionAvailabilityChanged
```

## See also

#### Reference

[Channel class](channel-class-microsoft-lync-model-conversation-audiovideo_2.md)

[Channel members](channel-members-microsoft-lync-model-conversation-audiovideo_2.md)

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

