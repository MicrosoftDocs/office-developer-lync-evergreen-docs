---
title: LyncServiceProvider.GetProvider method  (Microsoft.Lync.Controls)
TOCTitle: 'GetProvider method '
ms:assetid: M:Microsoft.Lync.Controls.LyncServiceProvider.GetProvider(System.Windows.DependencyObject)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.lyncserviceprovider.getprovider(v=office.15)
ms:contentKeyID: 48596354
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.LyncServiceProvider.GetProvider
dev_langs:
- CSharp
- JScript
- VB
- other
---

# LyncServiceProvider.GetProvider method

Get the **\[IUCClientModel\]** for the dependencyObject

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Shared Function GetProvider ( _
    dependencyObject As DependencyObject _
) As IUCClientModel
'Usage
Dim dependencyObject As DependencyObject
Dim returnValue As IUCClientModel

returnValue = LyncServiceProvider.GetProvider(dependencyObject)
```

``` csharp
public static IUCClientModel GetProvider(
    DependencyObject dependencyObject
)
```

#### Parameters

  - dependencyObject  
    Type: [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  

#### Return value

Type: **IUCClientModel**  

## See also

#### Reference

[LyncServiceProvider class](lyncserviceprovider-class-microsoft-lync-controls_1.md)

[LyncServiceProvider members](lyncserviceprovider-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

