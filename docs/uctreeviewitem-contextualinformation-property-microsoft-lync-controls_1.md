---
title: UCTreeViewItem.ContextualInformation property  (Microsoft.Lync.Controls)
TOCTitle: 'ContextualInformation property '
ms:assetid: P:Microsoft.Lync.Controls.UCTreeViewItem.ContextualInformation_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.uctreeviewitem.contextualinformation_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48588643
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.UCTreeViewItem.ContextualInformation
dev_langs:
- CSharp
- JScript
- VB
- other
---

# UCTreeViewItem.ContextualInformation property

Gets or sets data structure which provides contextual information for use with the contextual conversation feature.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property ContextualInformation As ConversationContextualInfo
    Get
    Set
'Usage
Dim instance As UCTreeViewItem
Dim value As ConversationContextualInfo

value = instance.ContextualInformation

instance.ContextualInformation = value
```

``` csharp
public ConversationContextualInfo ContextualInformation { get; set; }
```

#### Property value

Type: [Microsoft.Lync.Controls.ConversationContextualInfo](conversationcontextualinfo-class-microsoft-lync-controls_1.md)  

## Remarks

Contextual information is provided to the destination user when a conversation is initiated. This information may include a link or subject line which provides background on the purpose of a conversation. Optionally, context may be delivered in the form of an application reference and embedded application data. For more information, please refer to the related conceptual topics in the Lync SDK documentation.

## See also

#### Reference

[UCTreeViewItem class](uctreeviewitem-class-microsoft-lync-controls_1.md)

[UCTreeViewItem members](uctreeviewitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

