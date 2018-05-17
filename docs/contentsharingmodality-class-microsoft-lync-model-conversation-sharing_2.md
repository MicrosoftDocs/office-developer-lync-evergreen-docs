---
title: ContentSharingModality class (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ContentSharingModality class
ms:assetid: T:Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.contentsharingmodality_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590023
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContentSharingModality class

Creates and manages a collection of shareable content items.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWFull**  
        [Microsoft.Lync.Model.Conversation.Modality](modality-class-microsoft-lync-model-conversation_2.md)  
          Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality  

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class ContentSharingModality _
    Inherits Modality
'Usage
Dim instance As ContentSharingModality
```

``` csharp
public class ContentSharingModality : Modality
```

## Remarks

The ContentSharingModality inherits the methods, properties, and events from the Modality class. If you are sharing a whiteboard session with annotations in a conversation and then disconnect the ContentSharingModality, all of the whiteboard annotations are lost unless you save the whiteboard and associated annotations to a local file first.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContentSharingModality members](contentsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

