---
title: Self.BeginPublishContactInformation method  (Microsoft.Lync.Model)
TOCTitle: 'BeginPublishContactInformation method '
ms:assetid: M:Microsoft.Lync.Model.Self.BeginPublishContactInformation(System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{Microsoft.Lync.Model.PublishableContactInformationType,System.Object}},System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.self.beginpublishcontactinformation(v=office.15)
ms:contentKeyID: 48599894
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Self.BeginPublishContactInformation
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Self.BeginPublishContactInformation method

Starts the contact information publication operation. Used to publish a local users contact information.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginPublishContactInformation ( _
    items As IEnumerable(Of KeyValuePair(Of PublishableContactInformationType, Object)), _
    selfCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Self
Dim items As IEnumerable(Of KeyValuePair(Of PublishableContactInformationType, Object))
Dim selfCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginPublishContactInformation(items, _
    selfCallback, state)
```

``` csharp
public IAsyncResult BeginPublishContactInformation(
    IEnumerable<KeyValuePair<PublishableContactInformationType, Object>> items,
    AsyncCallback selfCallback,
    Object state
)
```

#### Parameters

  - items  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[KeyValuePair](http://msdn2.microsoft.com/en-us/library/5tbh8a42)\<[PublishableContactInformationType](publishablecontactinformationtype-enumeration-microsoft-lync-model_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>\>  

<!-- end list -->

  - selfCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Self class](self-class-microsoft-lync-model_2.md)

[Self members](self-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

