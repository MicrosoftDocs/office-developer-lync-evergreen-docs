---
title: LyncClient.CreateApplicationRegistration method  (Microsoft.Lync.Model)
TOCTitle: 'CreateApplicationRegistration method '
ms:assetid: M:Microsoft.Lync.Model.LyncClient.CreateApplicationRegistration(System.String,System.String)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclient.createapplicationregistration(v=office.15)
ms:contentKeyID: 48593917
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.LyncClient.CreateApplicationRegistration
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncClient.CreateApplicationRegistration method

Construct an application registration object used to register a Silverlight conversation window extension application.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CreateApplicationRegistration ( _
    appGuid As String, _
    appName As String _
) As ApplicationRegistration
'Usage
Dim instance As LyncClient
Dim appGuid As String
Dim appName As String
Dim returnValue As ApplicationRegistration

returnValue = instance.CreateApplicationRegistration(appGuid, _
    appName)
```

``` csharp
public ApplicationRegistration CreateApplicationRegistration(
    string appGuid,
    string appName
)
```

#### Parameters

  - appGuid  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - appName  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

#### Return value

Type: [Microsoft.Lync.Model.Extensibility.ApplicationRegistration](applicationregistration-class-microsoft-lync-model-extensibility_2.md)  
ApplicationRegistration.  

## See also

#### Reference

[LyncClient class](lyncclient-class-microsoft-lync-model_2.md)

[LyncClient members](lyncclient-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

