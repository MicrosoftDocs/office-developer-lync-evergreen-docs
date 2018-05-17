---
title: ConversationWindowInformationDictionary.Item property  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'Item property '
ms:assetid: P:Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary.Item(Microsoft.Lync.Model.Extensibility.ConversationWindowInformationType)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindowinformationdictionary.item(v=office.15)
ms:contentKeyID: 48598526
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary.Item
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindowInformationDictionary.Item property

Given a conversation window property type, returns the related item value.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Default Property Item ( _
    _key As ConversationWindowInformationType _
) As Object
    Get
    Set
'Usage
Dim instance As ConversationWindowInformationDictionary
Dim _key As ConversationWindowInformationType
Dim value As Object

value = instance(_key)

instance(_key) = value
```

``` csharp
public Object this[
    ConversationWindowInformationType _key
] { get; set; }
```

#### Parameters

  - \_key  
    Type: [Microsoft.Lync.Model.Extensibility.ConversationWindowInformationType](conversationwindowinformationtype-enumeration-microsoft-lync-model-extensibility_2.md)  

#### Property value

Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Implements

[IDictionary\<TKey, TValue\>.Item\[TKey\]](http://msdn2.microsoft.com/en-us/library/zyxt2e2h)  

## See also

#### Reference

[ConversationWindowInformationDictionary class](conversationwindowinformationdictionary-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindowInformationDictionary members](conversationwindowinformationdictionary-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

