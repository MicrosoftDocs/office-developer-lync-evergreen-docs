---
title: Conversation.BeginUnmuteParticipants method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginUnmuteParticipants method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.BeginUnmuteParticipants(System.Collections.Generic.IEnumerable{Microsoft.Lync.Model.Conversation.Participant},System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.beginunmuteparticipants(v=office.15)
ms:contentKeyID: 48600491
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.BeginUnmuteParticipants
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.BeginUnmuteParticipants method

Used to unmute a set of participants in a conference.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginUnmuteParticipants ( _
    participants As IEnumerable(Of Participant), _
    conversationCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Conversation
Dim participants As IEnumerable(Of Participant)
Dim conversationCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginUnmuteParticipants(participants, _
    conversationCallback, state)
```

``` csharp
public IAsyncResult BeginUnmuteParticipants(
    IEnumerable<Participant> participants,
    AsyncCallback conversationCallback,
    Object state
)
```

#### Parameters

  - participants  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[Participant](participant-class-microsoft-lync-model-conversation_2.md)\>  

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

