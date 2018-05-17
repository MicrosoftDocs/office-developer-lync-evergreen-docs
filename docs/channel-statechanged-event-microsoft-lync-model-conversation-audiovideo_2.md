---
title: Channel.StateChanged event (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: StateChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.AudioVideo.Channel.StateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.channel.statechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600904
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.Channel.StateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Channel.StateChanged event

Raised when the state of a channel changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event StateChanged As EventHandler(Of ChannelStateChangedEventArgs)
'Usage
Dim instance As Channel
Dim handler As EventHandler(Of ChannelStateChangedEventArgs)

AddHandler instance.StateChanged, handler
```

``` csharp
public event EventHandler<ChannelStateChangedEventArgs> StateChanged
```

## See also

#### Reference

[Channel class](channel-class-microsoft-lync-model-conversation-audiovideo_2.md)

[Channel members](channel-members-microsoft-lync-model-conversation-audiovideo_2.md)

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

