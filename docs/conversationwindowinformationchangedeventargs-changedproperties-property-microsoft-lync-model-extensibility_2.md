---
title: ConversationWindowInformationChangedEventArgs.ChangedProperties property  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'ChangedProperties property '
ms:assetid: P:Microsoft.Lync.Model.Extensibility.ConversationWindowInformationChangedEventArgs.ChangedProperties_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindowinformationchangedeventargs.changedproperties_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599440
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindowInformationChangedEventArgs.ChangedProperties
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindowInformationChangedEventArgs.ChangedProperties property

Returns a dictionary of conversation window properties that have changed.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property ChangedProperties As IDictionary(Of ConversationWindowInformationType, Object)
    Get
'Usage
Dim instance As ConversationWindowInformationChangedEventArgs
Dim value As IDictionary(Of ConversationWindowInformationType, Object)

value = instance.ChangedProperties
```

``` csharp
public IDictionary<ConversationWindowInformationType, Object> ChangedProperties { get; }
```

#### Property value

Type: [System.Collections.Generic.IDictionary](http://msdn2.microsoft.com/en-us/library/s4ys34ea)\<[ConversationWindowInformationType](conversationwindowinformationtype-enumeration-microsoft-lync-model-extensibility_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>  

## See also

#### Reference

[ConversationWindowInformationChangedEventArgs class](conversationwindowinformationchangedeventargs-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindowInformationChangedEventArgs members](conversationwindowinformationchangedeventargs-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

