---
title: ConversationWindowInformationDictionary.Contains method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'Contains method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary.Contains(System.Collections.Generic.KeyValuePair{Microsoft.Lync.Model.Extensibility.ConversationWindowInformationType,System.Object})_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindowinformationdictionary.contains(v=office.15)
ms:contentKeyID: 48590585
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary.Contains
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindowInformationDictionary.Contains method

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function Contains ( _
    item As KeyValuePair(Of ConversationWindowInformationType, Object) _
) As Boolean
'Usage
Dim instance As ConversationWindowInformationDictionary
Dim item As KeyValuePair(Of ConversationWindowInformationType, Object)
Dim returnValue As Boolean

returnValue = instance.Contains(item)
```

``` csharp
public bool Contains(
    KeyValuePair<ConversationWindowInformationType, Object> item
)
```

#### Parameters

  - item  
    Type: [System.Collections.Generic.KeyValuePair](http://msdn2.microsoft.com/en-us/library/5tbh8a42)\<[ConversationWindowInformationType](conversationwindowinformationtype-enumeration-microsoft-lync-model-extensibility_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

#### Implements

[ICollection\<T\>.Contains(T)](http://msdn2.microsoft.com/en-us/library/k5cf1d56)  

## See also

#### Reference

[ConversationWindowInformationDictionary class](conversationwindowinformationdictionary-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindowInformationDictionary members](conversationwindowinformationdictionary-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

