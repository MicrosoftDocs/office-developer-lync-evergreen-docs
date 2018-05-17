---
title: Automation.BeginStartConversation method (String, Int64, AsyncCallback, Object) (Microsoft.Lync.Model.Extensibility)
TOCTitle: BeginStartConversation method (String, Int64, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Extensibility.Automation.BeginStartConversation(System.String,System.Int64,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.automation.beginstartconversation(v=office.15)
ms:contentKeyID: 56371190
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Automation.BeginStartConversation method (String, Int64, AsyncCallback, Object)

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginStartConversation ( _
    conferenceUrl As String, _
    parentHWND As Long, _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Automation
Dim conferenceUrl As String
Dim parentHWND As Long
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginStartConversation(conferenceUrl, _
    parentHWND, callback, state)
```

``` csharp
public IAsyncResult BeginStartConversation(
    string conferenceUrl,
    long parentHWND,
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - conferenceUrl  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - parentHWND  
    Type: [System.Int64](http://msdn2.microsoft.com/en-us/library/6yy583ek)  

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

