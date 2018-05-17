---
title: Conversation.BeginPark method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginPark method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.BeginPark(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.beginpark(v=office.15)
ms:contentKeyID: 48590002
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.BeginPark
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.BeginPark method

Parks voice at the Call Park Server and terminates all other modalities.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginPark ( _
    conversationCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Conversation
Dim conversationCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginPark(conversationCallback, _
    state)
```

``` csharp
public IAsyncResult BeginPark(
    AsyncCallback conversationCallback,
    Object state
)
```

#### Parameters

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

