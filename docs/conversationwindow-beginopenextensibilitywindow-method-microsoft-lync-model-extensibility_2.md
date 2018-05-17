---
title: ConversationWindow.BeginOpenExtensibilityWindow method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'BeginOpenExtensibilityWindow method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.ConversationWindow.BeginOpenExtensibilityWindow(System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindow.beginopenextensibilitywindow(v=office.15)
ms:contentKeyID: 48601039
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindow.BeginOpenExtensibilityWindow
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindow.BeginOpenExtensibilityWindow method

Show the extensibility window for a registered application.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginOpenExtensibilityWindow ( _
    applicationId As String, _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ConversationWindow
Dim applicationId As String
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginOpenExtensibilityWindow(applicationId, _
    callback, state)
```

``` csharp
public IAsyncResult BeginOpenExtensibilityWindow(
    string applicationId,
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - applicationId  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

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

[ConversationWindow class](conversationwindow-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindow members](conversationwindow-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

