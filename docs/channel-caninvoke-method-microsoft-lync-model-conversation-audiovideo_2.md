---
title: Channel.CanInvoke method  (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: 'CanInvoke method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.AudioVideo.Channel.CanInvoke(Microsoft.Lync.Model.Conversation.AudioVideo.ChannelAction)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.channel.caninvoke(v=office.15)
ms:contentKeyID: 48602066
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.Channel.CanInvoke
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Channel.CanInvoke method

Returns a flag indicating whether the specific action is allowed.

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanInvoke ( _
    action As ChannelAction _
) As Boolean
'Usage
Dim instance As Channel
Dim action As ChannelAction
Dim returnValue As Boolean

returnValue = instance.CanInvoke(action)
```

``` csharp
public bool CanInvoke(
    ChannelAction action
)
```

#### Parameters

  - action  
    Type: [Microsoft.Lync.Model.Conversation.AudioVideo.ChannelAction](channelaction-enumeration-microsoft-lync-model-conversation-audiovideo_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## See also

#### Reference

[Channel class](channel-class-microsoft-lync-model-conversation-audiovideo_2.md)

[Channel members](channel-members-microsoft-lync-model-conversation-audiovideo_2.md)

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

