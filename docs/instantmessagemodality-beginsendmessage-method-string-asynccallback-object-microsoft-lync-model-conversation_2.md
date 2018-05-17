---
title: InstantMessageModality.BeginSendMessage method (String, AsyncCallback, Object) (Microsoft.Lync.Model.Conversation)
TOCTitle: BeginSendMessage method (String, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Conversation.InstantMessageModality.BeginSendMessage(System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.instantmessagemodality.beginsendmessage(v=office.15)
ms:contentKeyID: 48594971
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# InstantMessageModality.BeginSendMessage method (String, AsyncCallback, Object)

Sends a plain text message to a remote conversation participant.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSendMessage ( _
    text As String, _
    modalityCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As InstantMessageModality
Dim text As String
Dim modalityCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSendMessage(text, _
    modalityCallback, state)
```

``` csharp
public IAsyncResult BeginSendMessage(
    string text,
    AsyncCallback modalityCallback,
    Object state
)
```

#### Parameters

  - text  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - modalityCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[InstantMessageModality class](instantmessagemodality-class-microsoft-lync-model-conversation_2.md)

[InstantMessageModality members](instantmessagemodality-members-microsoft-lync-model-conversation_2.md)

[BeginSendMessage overload](instantmessagemodality-beginsendmessage-method-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

