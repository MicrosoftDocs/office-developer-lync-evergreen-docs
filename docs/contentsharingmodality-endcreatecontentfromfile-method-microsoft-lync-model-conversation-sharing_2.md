---
title: ContentSharingModality.EndCreateContentFromFile method  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'EndCreateContentFromFile method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.EndCreateContentFromFile(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.contentsharingmodality.endcreatecontentfromfile(v=office.15)
ms:contentKeyID: 48593769
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.EndCreateContentFromFile
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContentSharingModality.EndCreateContentFromFile method

Creates a content object of the given type with the given title and file name.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndCreateContentFromFile ( _
    asyncResult As IAsyncResult _
) As ShareableContent
'Usage
Dim instance As ContentSharingModality
Dim asyncResult As IAsyncResult
Dim returnValue As ShareableContent

returnValue = instance.EndCreateContentFromFile(asyncResult)
```

``` csharp
public ShareableContent EndCreateContentFromFile(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](shareablecontent-class-microsoft-lync-model-conversation-sharing_2.md)  

## See also

#### Reference

[ContentSharingModality class](contentsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ContentSharingModality members](contentsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

