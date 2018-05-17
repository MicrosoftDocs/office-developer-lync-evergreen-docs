---
title: Conversation.EndSetProperty method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'EndSetProperty method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.EndSetProperty(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.endsetproperty(v=office.15)
ms:contentKeyID: 48589306
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.EndSetProperty
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.EndSetProperty method

Sets a property associated with this conversation. This is an asynchronous operation, hence the conversationCallback, if specified, will be called back.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndSetProperty ( _
    asyncResult As IAsyncResult _
) As ConversationProperty
'Usage
Dim instance As Conversation
Dim asyncResult As IAsyncResult
Dim returnValue As ConversationProperty

returnValue = instance.EndSetProperty(asyncResult)
```

``` csharp
public ConversationProperty EndSetProperty(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Conversation.ConversationProperty](conversationproperty-enumeration-microsoft-lync-model-conversation_2.md)  

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

