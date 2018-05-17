---
title: ApplicationRegistration.SetExtensibilityWindowProperties method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'SetExtensibilityWindowProperties method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.ApplicationRegistration.SetExtensibilityWindowProperties(System.String,System.String,Microsoft.Lync.Model.Extensibility.ConversationWindowExtensionSize)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.applicationregistration.setextensibilitywindowproperties(v=office.15)
ms:contentKeyID: 48601805
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ApplicationRegistration.SetExtensibilityWindowProperties
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ApplicationRegistration.SetExtensibilityWindowProperties method

Sets the extensibility window properties.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub SetExtensibilityWindowProperties ( _
    intrnalUrl As String, _
    externalUrl As String, _
    windowSize As ConversationWindowExtensionSize _
)
'Usage
Dim instance As ApplicationRegistration
Dim intrnalUrl As String
Dim externalUrl As String
Dim windowSize As ConversationWindowExtensionSize

instance.SetExtensibilityWindowProperties(intrnalUrl, _
    externalUrl, windowSize)
```

``` csharp
public void SetExtensibilityWindowProperties(
    string intrnalUrl,
    string externalUrl,
    ConversationWindowExtensionSize windowSize
)
```

#### Parameters

  - intrnalUrl  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - externalUrl  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - windowSize  
    Type: [Microsoft.Lync.Model.Extensibility.ConversationWindowExtensionSize](conversationwindowextensionsize-enumeration-microsoft-lync-model-extensibility_2.md)  

## See also

#### Reference

[ApplicationRegistration class](applicationregistration-class-microsoft-lync-model-extensibility_2.md)

[ApplicationRegistration members](applicationregistration-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

