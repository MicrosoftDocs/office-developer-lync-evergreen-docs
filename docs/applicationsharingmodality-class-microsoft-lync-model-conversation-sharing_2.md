---
title: ApplicationSharingModality class (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ApplicationSharingModality class
ms:assetid: T:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingmodality_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594961
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ApplicationSharingModality class

Represents the application sharing modality of a conversation or participant modality collection.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWFull**  
        [Microsoft.Lync.Model.Conversation.Modality](modality-class-microsoft-lync-model-conversation_2.md)  
          Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality  

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class ApplicationSharingModality _
    Inherits Modality
'Usage
Dim instance As ApplicationSharingModality
```

``` csharp
public class ApplicationSharingModality : Modality
```

## Remarks

Use the ApplicationSharingModality from a participant modality collection when you want to take some controlling action for that participant on the shared resource. For example, if you want to grant control of a shared resource to a participant, you call BeginGrantControl on that participant modality.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ApplicationSharingModality members](applicationsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

