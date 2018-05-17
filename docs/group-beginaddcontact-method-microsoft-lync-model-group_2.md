---
title: Group.BeginAddContact method  (Microsoft.Lync.Model.Group)
TOCTitle: 'BeginAddContact method '
ms:assetid: M:Microsoft.Lync.Model.Group.Group.BeginAddContact(Microsoft.Lync.Model.Contact,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.group.beginaddcontact(v=office.15)
ms:contentKeyID: 48595253
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.Group.BeginAddContact
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Group.BeginAddContact method

Adds a new contact to the group.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginAddContact ( _
    contact As Contact, _
    groupCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Group
Dim contact As Contact
Dim groupCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginAddContact(contact, _
    groupCallback, state)
```

``` csharp
public IAsyncResult BeginAddContact(
    Contact contact,
    AsyncCallback groupCallback,
    Object state
)
```

#### Parameters

  - contact  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

<!-- end list -->

  - groupCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Group class](group-class-microsoft-lync-model-group_2.md)

[Group members](group-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

