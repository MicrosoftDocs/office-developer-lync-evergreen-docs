---
title: ContentSharingModality.BeginCreateContent method  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'BeginCreateContent method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.BeginCreateContent(Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType,System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.contentsharingmodality.begincreatecontent(v=office.15)
ms:contentKeyID: 48599094
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.BeginCreateContent
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContentSharingModality.BeginCreateContent method

Creates a content object of the given type with the given title

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginCreateContent ( _
    contentType As ShareableContentType, _
    title As String, _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ContentSharingModality
Dim contentType As ShareableContentType
Dim title As String
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginCreateContent(contentType, _
    title, callback, state)
```

``` csharp
public IAsyncResult BeginCreateContent(
    ShareableContentType contentType,
    string title,
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - contentType  
    Type: [Microsoft.Lync.Model.Conversation.Sharing.ShareableContentType](shareablecontenttype-enumeration-microsoft-lync-model-conversation-sharing_2.md)  

<!-- end list -->

  - title  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - callback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[ContentSharingModality class](contentsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ContentSharingModality members](contentsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

