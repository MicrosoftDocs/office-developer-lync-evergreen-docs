---
title: ConversationWindowInformationDictionary class (Microsoft.Lync.Model.Extensibility)
TOCTitle: ConversationWindowInformationDictionary class
ms:assetid: T:Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindowinformationdictionary_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594868
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindowInformationDictionary class

A dictionary that contains a collection of information items for a conversation window.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWLite**  
        Microsoft.Lync.Model.Extensibility.ConversationWindowInformationDictionary  

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class ConversationWindowInformationDictionary _
    Inherits UCWLite _
    Implements IDictionary(Of ConversationWindowInformationType, Object),  _
    ICollection(Of KeyValuePair(Of ConversationWindowInformationType, Object)), IEnumerable(Of KeyValuePair(Of ConversationWindowInformationType, Object)),  _
    IEnumerable
'Usage
Dim instance As ConversationWindowInformationDictionary
```

``` csharp
public class ConversationWindowInformationDictionary : UCWLite, 
    IDictionary<ConversationWindowInformationType, Object>, ICollection<KeyValuePair<ConversationWindowInformationType, Object>>, 
    IEnumerable<KeyValuePair<ConversationWindowInformationType, Object>>, IEnumerable
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ConversationWindowInformationDictionary members](conversationwindowinformationdictionary-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

