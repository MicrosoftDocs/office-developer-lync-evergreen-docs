---
title: Utilities.BeginAddToExternalContacts method  (Microsoft.Lync.Model)
TOCTitle: 'BeginAddToExternalContacts method '
ms:assetid: M:Microsoft.Lync.Model.Utilities.BeginAddToExternalContacts(Microsoft.Lync.Model.Contact,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.utilities.beginaddtoexternalcontacts(v=office.15)
ms:contentKeyID: 48601927
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Utilities.BeginAddToExternalContacts
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Utilities.BeginAddToExternalContacts method

Add the contact into external provider contacts

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginAddToExternalContacts ( _
    contactContext As Contact, _
    utilitiesCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Utilities
Dim contactContext As Contact
Dim utilitiesCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginAddToExternalContacts(contactContext, _
    utilitiesCallback, state)
```

``` csharp
public IAsyncResult BeginAddToExternalContacts(
    Contact contactContext,
    AsyncCallback utilitiesCallback,
    Object state
)
```

#### Parameters

  - contactContext  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

<!-- end list -->

  - utilitiesCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Utilities class](utilities-class-microsoft-lync-model_2.md)

[Utilities members](utilities-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

