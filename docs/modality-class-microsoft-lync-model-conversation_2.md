---
title: Modality class (Microsoft.Lync.Model.Conversation)
TOCTitle: Modality class
ms:assetid: T:Microsoft.Lync.Model.Conversation.Modality_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48593424
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Modality
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Modality class

Modality is the base class for any modality, including InstantMessageModality and AVModality.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWFull**  
        Microsoft.Lync.Model.Conversation.Modality  
          [Microsoft.Lync.Model.Conversation.AudioVideo.AVModality](avmodality-class-microsoft-lync-model-conversation-audiovideo_2.md)  
          [Microsoft.Lync.Model.Conversation.InstantMessageModality](instantmessagemodality-class-microsoft-lync-model-conversation_2.md)  
          [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)  
          [Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality](contentsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)  

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public MustInherit Class Modality _
    Inherits UCWFull
'Usage
Dim instance As Modality
```

``` csharp
public abstract class Modality : UCWFull
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[Modality members](modality-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

