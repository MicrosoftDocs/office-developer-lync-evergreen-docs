---
title: Conversation.BeginSendContextData method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginSendContextData method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.BeginSendContextData(System.String,System.String,System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.beginsendcontextdata(v=office.15)
ms:contentKeyID: 48600270
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.BeginSendContextData
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.BeginSendContextData method

This is used to send application context type and data to the conversation. The application Id has to be registered on the caller side. The context data will be sent in raw foramts

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSendContextData ( _
    applicationId As String, _
    dataType As String, _
    data As String, _
    conversationCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Conversation
Dim applicationId As String
Dim dataType As String
Dim data As String
Dim conversationCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSendContextData(applicationId, _
    dataType, data, conversationCallback, _
    state)
```

``` csharp
public IAsyncResult BeginSendContextData(
    string applicationId,
    string dataType,
    string data,
    AsyncCallback conversationCallback,
    Object state
)
```

#### Parameters

  - applicationId  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - dataType  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - data  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

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

