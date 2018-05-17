---
title: ContactManager.BeginSearch method (String, SearchProviders, SearchFields, SearchOptions, UInt32, AsyncCallback, Object) (Microsoft.Lync.Model)
TOCTitle: BeginSearch method (String, SearchProviders, SearchFields, SearchOptions, UInt32, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.ContactManager.BeginSearch(System.String,Microsoft.Lync.Model.SearchProviders,Microsoft.Lync.Model.SearchFields,Microsoft.Lync.Model.SearchOptions,System.UInt32,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.beginsearch(v=office.15)
ms:contentKeyID: 48591239
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# ContactManager.BeginSearch method (String, SearchProviders, SearchFields, SearchOptions, UInt32, AsyncCallback, Object)

Searches for contacts and distribution groups that match the given search criteria.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSearch ( _
    searchString As String, _
    providers As SearchProviders, _
    searchFields As SearchFields, _
    searchOptions As SearchOptions, _
    maxResults As UInteger, _
    contactsAndGroupsCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As ContactManager
Dim searchString As String
Dim providers As SearchProviders
Dim searchFields As SearchFields
Dim searchOptions As SearchOptions
Dim maxResults As UInteger
Dim contactsAndGroupsCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSearch(searchString, _
    providers, searchFields, searchOptions, _
    maxResults, contactsAndGroupsCallback, _
    state)
```

``` csharp
public IAsyncResult BeginSearch(
    string searchString,
    SearchProviders providers,
    SearchFields searchFields,
    SearchOptions searchOptions,
    uint maxResults,
    AsyncCallback contactsAndGroupsCallback,
    Object state
)
```

#### Parameters

  - searchString  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - providers  
    Type: [Microsoft.Lync.Model.SearchProviders](searchproviders-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - searchFields  
    Type: [Microsoft.Lync.Model.SearchFields](searchfields-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - searchOptions  
    Type: [Microsoft.Lync.Model.SearchOptions](searchoptions-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - maxResults  
    Type: [System.UInt32](http://msdn2.microsoft.com/en-us/library/ctys3981)  

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

