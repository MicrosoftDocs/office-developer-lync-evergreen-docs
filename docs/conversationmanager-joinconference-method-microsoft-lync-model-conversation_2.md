---
title: ConversationManager.JoinConference method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'JoinConference method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.ConversationManager.JoinConference(System.String)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversationmanager.joinconference(v=office.15)
ms:contentKeyID: 48597358
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.ConversationManager.JoinConference
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationManager.JoinConference method

Retrieves/Creates a conversation initialized so as to join conference at given URL.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function JoinConference ( _
    conferenceUrl As String _
) As Conversation
'Usage
Dim instance As ConversationManager
Dim conferenceUrl As String
Dim returnValue As Conversation

returnValue = instance.JoinConference(conferenceUrl)
```

``` csharp
public Conversation JoinConference(
    string conferenceUrl
)
```

#### Parameters

  - conferenceUrl  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

#### Return value

Type: [Microsoft.Lync.Model.Conversation.Conversation](conversation-class-microsoft-lync-model-conversation_2.md)  
Microsoft.Lync.Model.Conversation.Conversation  

## See also

#### Reference

[ConversationManager class](conversationmanager-class-microsoft-lync-model-conversation_2.md)

[ConversationManager members](conversationmanager-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

