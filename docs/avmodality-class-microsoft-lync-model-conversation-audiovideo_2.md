---
title: AVModality class (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: AVModality class
ms:assetid: T:Microsoft.Lync.Model.Conversation.AudioVideo.AVModality_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.avmodality_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592933
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.AVModality
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AVModality class

Defines the audio/video modality and handles both audio and video calls using the AudioChannel and VideoChannel properties.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWFull**  
        [Microsoft.Lync.Model.Conversation.Modality](modality-class-microsoft-lync-model-conversation_2.md)  
          Microsoft.Lync.Model.Conversation.AudioVideo.AVModality  

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class AVModality _
    Inherits Modality
'Usage
Dim instance As AVModality
```

``` csharp
public class AVModality : Modality
```

## Remarks

When the AVModality is connected, the default channel is audio. Starting the video channel will cause the audio channel to start if the modality is disconnected. If the AV call is rejected with a reject reason of ReplyOther, the parent Conversation object is removed and the ConversationManager.ConversationRemoved event is raised.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[AVModality members](avmodality-members-microsoft-lync-model-conversation-audiovideo_2.md)

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

