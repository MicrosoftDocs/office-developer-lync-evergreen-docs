---
title: Modality.Accept method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'Accept method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Modality.Accept_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.accept_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596250
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Modality.Accept
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Modality.Accept method

Accept an offer for the modality.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub Accept
'Usage
Dim instance As Modality

instance.Accept()
```

``` csharp
public void Accept()
```

## Remarks

Call Accept() on the participant modality that made the offer. For exa mple, when a remote participant offers to share a whiteboard in a meeting, call ContentSharingModality.Accept() on the ContentSharingModality object in the remote participant modalities collection.

## See also

#### Reference

[Modality class](modality-class-microsoft-lync-model-conversation_2.md)

[Modality members](modality-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

