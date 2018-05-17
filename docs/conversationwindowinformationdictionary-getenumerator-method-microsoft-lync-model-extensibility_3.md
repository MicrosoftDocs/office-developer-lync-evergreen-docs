---
title: ConversationWindowInformationDictionary.GetEnumerator method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'GetEnumerator method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary.GetEnumerator_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindowinformationdictionary.getenumerator_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592756
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary.GetEnumerator
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindowInformationDictionary.GetEnumerator method

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetEnumerator As IEnumerator(Of KeyValuePair(Of ConversationWindowInformationType, Object))
'Usage
Dim instance As ConversationWindowInformationDictionary
Dim returnValue As IEnumerator(Of KeyValuePair(Of ConversationWindowInformationType, Object))

returnValue = instance.GetEnumerator()
```

``` csharp
public IEnumerator<KeyValuePair<ConversationWindowInformationType, Object>> GetEnumerator()
```

#### Return value

Type: [System.Collections.Generic.IEnumerator](http://msdn2.microsoft.com/en-us/library/78dfe2yb)\<[KeyValuePair](http://msdn2.microsoft.com/en-us/library/5tbh8a42)\<[ConversationWindowInformationType](conversationwindowinformationtype-enumeration-microsoft-lync-model-extensibility_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>\>  

#### Implements

[IEnumerable\<T\>.GetEnumerator()](http://msdn2.microsoft.com/en-us/library/s793z9y2)  

## See also

#### Reference

[ConversationWindowInformationDictionary class](conversationwindowinformationdictionary-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindowInformationDictionary members](conversationwindowinformationdictionary-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

