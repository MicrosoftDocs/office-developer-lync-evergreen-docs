---
title: Utilities.BeginComposeEmail method (DistributionGroup, String, AsyncCallback, Object) (Microsoft.Lync.Model)
TOCTitle: BeginComposeEmail method (DistributionGroup, String, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Utilities.BeginComposeEmail(Microsoft.Lync.Model.Group.DistributionGroup,System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.utilities.begincomposeemail(v=office.15)
ms:contentKeyID: 48594528
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Utilities.BeginComposeEmail method (DistributionGroup, String, AsyncCallback, Object)

Launches a new Outlook message window pre-populated with the specified distribution group and subject string passed in the first two arguments of this method.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginComposeEmail ( _
    to As DistributionGroup, _
    subject As String, _
    utilitiesCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Utilities
Dim to As DistributionGroup
Dim subject As String
Dim utilitiesCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginComposeEmail(to, _
    subject, utilitiesCallback, state)
```

``` csharp
public IAsyncResult BeginComposeEmail(
    DistributionGroup to,
    string subject,
    AsyncCallback utilitiesCallback,
    Object state
)
```

#### Parameters

  - to  
    Type: [Microsoft.Lync.Model.Group.DistributionGroup](distributiongroup-class-microsoft-lync-model-group_2.md)  

<!-- end list -->

  - subject  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

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

[BeginComposeEmail overload](utilities-begincomposeemail-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

