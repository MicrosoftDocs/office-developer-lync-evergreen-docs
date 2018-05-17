---
title: ContactManager.BeginSearch method (String, AsyncCallback, Object) (Microsoft.Lync.Model)
TOCTitle: BeginSearch method (String, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.ContactManager.BeginSearch(System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.beginsearch(v=office.15)
ms:contentKeyID: 48601820
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# ContactManager.BeginSearch method (String, AsyncCallback, Object)

Begins to search for contacts or distribution groups matching a specified search string. Results of the search are returned in the System.AsyncCallback you pass in the contactsAndGroupsCallback argument.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSearch ( _
    searchString As String, _
    contactsAndGroupsCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ContactManager
Dim searchString As String
Dim contactsAndGroupsCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSearch(searchString, _
    contactsAndGroupsCallback, state)
```

``` csharp
public IAsyncResult BeginSearch(
    string searchString,
    AsyncCallback contactsAndGroupsCallback,
    Object state
)
```

#### Parameters

  - searchString  
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

[BeginSearch overload](contactmanager-beginsearch-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

