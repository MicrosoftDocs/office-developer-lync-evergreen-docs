---
title: Conversation.EndSendInitialContext method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'EndSendInitialContext method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.EndSendInitialContext(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.endsendinitialcontext(v=office.15)
ms:contentKeyID: 48593802
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.EndSendInitialContext
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.EndSendInitialContext method

This is used to send application context to the conversation. ContextTypes and contextDatas are mapped together, So they must have the same length.If the contextTypes include application GUID, the caller must have been registered using the same GUID.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub EndSendInitialContext ( _
    asyncResult As IAsyncResult _
)
'Usage
Dim instance As Conversation
Dim asyncResult As IAsyncResult

instance.EndSendInitialContext(asyncResult)
```

``` csharp
public void EndSendInitialContext(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

