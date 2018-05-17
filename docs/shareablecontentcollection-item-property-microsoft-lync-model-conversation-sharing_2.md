---
title: ShareableContentCollection.Item property  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'Item property '
ms:assetid: P:Microsoft.Lync.Model.Conversation.Sharing.ShareableContentCollection.Item(System.Int32)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.shareablecontentcollection.item(v=office.15)
ms:contentKeyID: 48598557
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContentCollection.Item
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ShareableContentCollection.Item property

Given an index, returns an item in the collection.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Default Property Item ( _
    index As Integer _
) As ShareableContent
    Get
    Set
'Usage
Dim instance As ShareableContentCollection
Dim index As Integer
Dim value As ShareableContent

value = instance(index)

instance(index) = value
```

``` csharp
public ShareableContent this[
    int index
] { get; set; }
```

#### Parameters

  - index  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

#### Property value

Type: [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](shareablecontent-class-microsoft-lync-model-conversation-sharing_2.md)  

#### Implements

[IList\<T\>.Item\[Int32\]](http://msdn2.microsoft.com/en-us/library/ewthkb10)  

## See also

#### Reference

[ShareableContentCollection class](shareablecontentcollection-class-microsoft-lync-model-conversation-sharing_2.md)

[ShareableContentCollection members](shareablecontentcollection-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

