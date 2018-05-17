---
title: ContactManager.BeginRemoveContactFromAllGroups method  (Microsoft.Lync.Model)
TOCTitle: 'BeginRemoveContactFromAllGroups method '
ms:assetid: M:Microsoft.Lync.Model.ContactManager.BeginRemoveContactFromAllGroups(Microsoft.Lync.Model.Contact,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.beginremovecontactfromallgroups(v=office.15)
ms:contentKeyID: 48596751
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactManager.BeginRemoveContactFromAllGroups
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactManager.BeginRemoveContactFromAllGroups method

Removes a contact from all groups except distribution groups.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginRemoveContactFromAllGroups ( _
    contact As Contact, _
    contactsAndGroupsCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ContactManager
Dim contact As Contact
Dim contactsAndGroupsCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginRemoveContactFromAllGroups(contact, _
    contactsAndGroupsCallback, state)
```

``` csharp
public IAsyncResult BeginRemoveContactFromAllGroups(
    Contact contact,
    AsyncCallback contactsAndGroupsCallback,
    Object state
)
```

#### Parameters

  - contact  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

<!-- end list -->

  - contactsAndGroupsCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

