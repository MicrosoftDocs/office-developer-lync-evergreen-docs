---
title: Conversation.CanSetProperty method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'CanSetProperty method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.CanSetProperty(Microsoft.Lync.Model.Conversation.ConversationProperty)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.cansetproperty(v=office.15)
ms:contentKeyID: 48588555
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.CanSetProperty
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.CanSetProperty method

Test whether the property can be set to the conversation.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanSetProperty ( _
    convProperty As ConversationProperty _
) As Boolean
'Usage
Dim instance As Conversation
Dim convProperty As ConversationProperty
Dim returnValue As Boolean

returnValue = instance.CanSetProperty(convProperty)
```

``` csharp
public bool CanSetProperty(
    ConversationProperty convProperty
)
```

#### Parameters

  - convProperty  
    Type: [Microsoft.Lync.Model.Conversation.ConversationProperty](conversationproperty-enumeration-microsoft-lync-model-conversation_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

