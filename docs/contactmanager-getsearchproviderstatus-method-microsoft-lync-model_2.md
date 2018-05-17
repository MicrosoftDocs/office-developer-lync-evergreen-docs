---
title: ContactManager.GetSearchProviderStatus method  (Microsoft.Lync.Model)
TOCTitle: 'GetSearchProviderStatus method '
ms:assetid: M:Microsoft.Lync.Model.ContactManager.GetSearchProviderStatus(Microsoft.Lync.Model.SearchProviders)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.getsearchproviderstatus(v=office.15)
ms:contentKeyID: 48591198
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactManager.GetSearchProviderStatus
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactManager.GetSearchProviderStatus method

Gets the search provider status.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetSearchProviderStatus ( _
    provider As SearchProviders _
) As SearchProviderStatusType
'Usage
Dim instance As ContactManager
Dim provider As SearchProviders
Dim returnValue As SearchProviderStatusType

returnValue = instance.GetSearchProviderStatus(provider)
```

``` csharp
public SearchProviderStatusType GetSearchProviderStatus(
    SearchProviders provider
)
```

#### Parameters

  - provider  
    Type: [Microsoft.Lync.Model.SearchProviders](searchproviders-enumeration-microsoft-lync-model_2.md)  

#### Return value

Type: [Microsoft.Lync.Model.SearchProviderStatusType](searchproviderstatustype-enumeration-microsoft-lync-model_2.md)  
Microsoft.Lync.Model.SearchProviderStatusType  

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

