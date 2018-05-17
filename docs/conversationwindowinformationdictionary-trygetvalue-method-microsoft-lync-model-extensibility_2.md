---
title: ConversationWindowInformationDictionary.TryGetValue method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'TryGetValue method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary.TryGetValue(Microsoft.Lync.Model.Extensibility.ConversationWindowInformationType,System.Object@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindowinformationdictionary.trygetvalue(v=office.15)
ms:contentKeyID: 48588588
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary.TryGetValue
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindowInformationDictionary.TryGetValue method

Tries to find a value for the given key.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function TryGetValue ( _
    key As ConversationWindowInformationType, _
    <OutAttribute> ByRef itemValue As Object _
) As Boolean
'Usage
Dim instance As ConversationWindowInformationDictionary
Dim key As ConversationWindowInformationType
Dim itemValue As Object
Dim returnValue As Boolean

returnValue = instance.TryGetValue(key, _
    itemValue)
```

``` csharp
public bool TryGetValue(
    ConversationWindowInformationType key,
    out Object itemValue
)
```

#### Parameters

  - key  
    Type: [Microsoft.Lync.Model.Extensibility.ConversationWindowInformationType](conversationwindowinformationtype-enumeration-microsoft-lync-model-extensibility_2.md)  

<!-- end list -->

  - itemValue  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

#### Implements

[IDictionary\<TKey, TValue\>.TryGetValue(TKey, TValue)](http://msdn2.microsoft.com/en-us/library/bb299639)  

## See also

#### Reference

[ConversationWindowInformationDictionary class](conversationwindowinformationdictionary-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindowInformationDictionary members](conversationwindowinformationdictionary-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

