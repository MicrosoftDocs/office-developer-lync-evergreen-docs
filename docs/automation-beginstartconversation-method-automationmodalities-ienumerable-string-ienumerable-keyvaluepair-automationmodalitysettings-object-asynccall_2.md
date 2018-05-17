---
title: Automation.BeginStartConversation method (AutomationModalities, IEnumerable(String), IEnumerable(KeyValuePair(AutomationModalitySettings, Object)), AsyncCallback, Object) (Microsoft.Lync.Model.Extensibility)
TOCTitle: BeginStartConversation method (AutomationModalities, IEnumerable(String), IEnumerable(KeyValuePair(AutomationModalitySettings, Object)), AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Extensibility.Automation.BeginStartConversation(Microsoft.Lync.Model.Extensibility.AutomationModalities,System.Collections.Generic.IEnumerable{System.String},System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{Microsoft.Lync.Model.Extensibility.AutomationModalitySettings,System.Object}},System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.automation.beginstartconversation(v=office.15)
ms:contentKeyID: 48601176
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Automation.BeginStartConversation method (AutomationModalities, IEnumerable\<String\>, IEnumerable\<KeyValuePair\<AutomationModalitySettings, Object\>\>, AsyncCallback, Object)

Launches a Lync conversation window and invites specified participants using the specified modalities and optional conversation context data. The new conversation window is obtained in the System.AsyncCallback method you pass in the callback argument.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginStartConversation ( _
    conversationModes As AutomationModalities, _
    participantUris As IEnumerable(Of String), _
    contextData As IEnumerable(Of KeyValuePair(Of AutomationModalitySettings, Object)), _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Automation
Dim conversationModes As AutomationModalities
Dim participantUris As IEnumerable(Of String)
Dim contextData As IEnumerable(Of KeyValuePair(Of AutomationModalitySettings, Object))
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginStartConversation(conversationModes, _
    participantUris, contextData, callback, _
    state)
```

``` csharp
public IAsyncResult BeginStartConversation(
    AutomationModalities conversationModes,
    IEnumerable<string> participantUris,
    IEnumerable<KeyValuePair<AutomationModalitySettings, Object>> contextData,
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - conversationModes  
    Type: [Microsoft.Lync.Model.Extensibility.AutomationModalities](automationmodalities-enumeration-microsoft-lync-model-extensibility_2.md)  

<!-- end list -->

  - participantUris  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)\>  

<!-- end list -->

  - contextData  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[KeyValuePair](http://msdn2.microsoft.com/en-us/library/5tbh8a42)\<[AutomationModalitySettings](automationmodalitysettings-enumeration-microsoft-lync-model-extensibility_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>\>  

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

[Automation class](automation-class-microsoft-lync-model-extensibility_2.md)

[Automation members](automation-members-microsoft-lync-model-extensibility_2.md)

[BeginStartConversation overload](automation-beginstartconversation-method-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

