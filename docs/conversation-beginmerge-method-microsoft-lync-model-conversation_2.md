---
title: Conversation.BeginMerge method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginMerge method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.BeginMerge(Microsoft.Lync.Model.Conversation.Conversation,Microsoft.Lync.Model.Conversation.ModalityTypes,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.beginmerge(v=office.15)
ms:contentKeyID: 48601164
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.BeginMerge
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.BeginMerge method

Merges another conversation into this one.modalityTypes specifies what modalities to be merged in.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginMerge ( _
    conversation As Conversation, _
    modalityTypes As ModalityTypes, _
    conversationCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Conversation
Dim conversation As Conversation
Dim modalityTypes As ModalityTypes
Dim conversationCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginMerge(conversation, _
    modalityTypes, conversationCallback, _
    state)
```

``` csharp
public IAsyncResult BeginMerge(
    Conversation conversation,
    ModalityTypes modalityTypes,
    AsyncCallback conversationCallback,
    Object state
)
```

#### Parameters

  - conversation  
    Type: [Microsoft.Lync.Model.Conversation.Conversation](conversation-class-microsoft-lync-model-conversation_2.md)  

<!-- end list -->

  - modalityTypes  
    Type: [Microsoft.Lync.Model.Conversation.ModalityTypes](modalitytypes-enumeration-microsoft-lync-model-conversation_2.md)  

<!-- end list -->

  - conversationCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

