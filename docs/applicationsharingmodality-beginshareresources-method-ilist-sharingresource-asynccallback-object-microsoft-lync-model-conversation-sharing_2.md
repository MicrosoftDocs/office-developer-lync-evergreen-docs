---
title: ApplicationSharingModality.BeginShareResources method (IList(SharingResource), AsyncCallback, Object) (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: BeginShareResources method (IList(SharingResource), AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.BeginShareResources(System.Collections.Generic.IList{Microsoft.Lync.Model.Conversation.Sharing.SharingResource},System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingmodality.beginshareresources(v=office.15)
ms:contentKeyID: 48601864
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# ApplicationSharingModality.BeginShareResources method (IList\<SharingResource\>, AsyncCallback, Object)

Starts sharing resources with the given a list of resources.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginShareResources ( _
    resourceList As IList(Of SharingResource), _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ApplicationSharingModality
Dim resourceList As IList(Of SharingResource)
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginShareResources(resourceList, _
    callback, state)
```

``` csharp
public IAsyncResult BeginShareResources(
    IList<SharingResource> resourceList,
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - resourceList  
    Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[SharingResource](sharingresource-class-microsoft-lync-model-conversation-sharing_2.md)\>  

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

[ApplicationSharingModality class](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ApplicationSharingModality members](applicationsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[BeginShareResources overload](applicationsharingmodality-beginshareresources-method-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

