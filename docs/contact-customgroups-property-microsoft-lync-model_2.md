---
title: Contact.CustomGroups property  (Microsoft.Lync.Model)
TOCTitle: 'CustomGroups property '
ms:assetid: P:Microsoft.Lync.Model.Contact.CustomGroups_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.customgroups_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600920
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.CustomGroups
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.CustomGroups property

Gets the list of all groups of which this contact is a member of.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property CustomGroups As GroupCollection
    Get
'Usage
Dim instance As Contact
Dim value As GroupCollection

value = instance.CustomGroups
```

``` csharp
public GroupCollection CustomGroups { get; }
```

#### Property value

Type: [Microsoft.Lync.Model.Group.GroupCollection](groupcollection-class-microsoft-lync-model-group_2.md)  

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

