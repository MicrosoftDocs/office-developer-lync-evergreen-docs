---
title: Channel.BeginStart method  (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: 'BeginStart method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.AudioVideo.Channel.BeginStart(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.channel.beginstart(v=office.15)
ms:contentKeyID: 48599560
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.Channel.BeginStart
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Channel.BeginStart method

Start the audio or video channel.

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginStart ( _
    mediaChannelCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Channel
Dim mediaChannelCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginStart(mediaChannelCallback, _
    state)
```

``` csharp
public IAsyncResult BeginStart(
    AsyncCallback mediaChannelCallback,
    Object state
)
```

#### Parameters

  - mediaChannelCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Channel class](channel-class-microsoft-lync-model-conversation-audiovideo_2.md)

[Channel members](channel-members-microsoft-lync-model-conversation-audiovideo_2.md)

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

