---
title: ContactManager.BeginAddGroup method (String, AsyncCallback, Object) (Microsoft.Lync.Model)
TOCTitle: BeginAddGroup method (String, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.ContactManager.BeginAddGroup(System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.beginaddgroup(v=office.15)
ms:contentKeyID: 48596731
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# ContactManager.BeginAddGroup method (String, AsyncCallback, Object)

Adds a new custom group to the group list.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginAddGroup ( _
    customGroupName As String, _
    contactsAndGroupsCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ContactManager
Dim customGroupName As String
Dim contactsAndGroupsCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginAddGroup(customGroupName, _
    contactsAndGroupsCallback, state)
```

``` csharp
public IAsyncResult BeginAddGroup(
    string customGroupName,
    AsyncCallback contactsAndGroupsCallback,
    Object state
)
```

#### Parameters

  - customGroupName  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

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

[BeginAddGroup overload](contactmanager-beginaddgroup-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

