---
title: ApplicationSharingModality.CanShare method (SharingResourceType, CanShareDetail) (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: CanShare method (SharingResourceType, CanShareDetail)
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.CanShare(Microsoft.Lync.Model.Conversation.Sharing.SharingResourceType,Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingmodality.canshare(v=office.15)
ms:contentKeyID: 48601470
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# ApplicationSharingModality.CanShare method (SharingResourceType, CanShareDetail)

Finds if the given resource type can be shared and provides some detail.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanShare ( _
    type As SharingResourceType, _
    <OutAttribute> ByRef detail As CanShareDetail _
) As Boolean
'Usage
Dim instance As ApplicationSharingModality
Dim type As SharingResourceType
Dim detail As CanShareDetail
Dim returnValue As Boolean

returnValue = instance.CanShare(type, _
    detail)
```

``` csharp
public bool CanShare(
    SharingResourceType type,
    out CanShareDetail detail
)
```

#### Parameters

  - type  
    Type: [Microsoft.Lync.Model.Conversation.Sharing.SharingResourceType](sharingresourcetype-enumeration-microsoft-lync-model-conversation-sharing_2.md)  

<!-- end list -->

  - detail  
    Type: [Microsoft.Lync.Model.Conversation.Sharing.CanShareDetail](cansharedetail-enumeration-microsoft-lync-model-conversation-sharing_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## See also

#### Reference

[ApplicationSharingModality class](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ApplicationSharingModality members](applicationsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[CanShare overload](applicationsharingmodality-canshare-method-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

