---
title: Automation.BeginMeetNow method (AsyncCallback, Object) (Microsoft.Lync.Model.Extensibility)
TOCTitle: BeginMeetNow method (AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Extensibility.Automation.BeginMeetNow(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.automation.beginmeetnow(v=office.15)
ms:contentKeyID: 48590592
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Automation.BeginMeetNow method (AsyncCallback, Object)

Launches a Lync Meet Now conversation window using the specified modalities. The new conversation window is obtained in the System.AsyncCallback method you pass in the callback argument.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginMeetNow ( _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Automation
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginMeetNow(callback, _
    state)
```

``` csharp
public IAsyncResult BeginMeetNow(
    AsyncCallback callback,
    Object state
)
```

#### Parameters

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

[BeginMeetNow overload](automation-beginmeetnow-method-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

