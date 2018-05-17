---
title: MyPresenceChooser class (Microsoft.Lync.Controls)
TOCTitle: MyPresenceChooser class
ms:assetid: T:Microsoft.Lync.Controls.MyPresenceChooser_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.mypresencechooser_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594466
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.MyPresenceChooser
dev_langs:
- CSharp
- JScript
- VB
- other
---

# MyPresenceChooser class

The MyPresenceChooser control displays and changes the user's current presence status selection.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [Microsoft.Lync.Controls.UCBase](ucbase-class-microsoft-lync-controls_1.md)  
                [Microsoft.Lync.Controls.SelfBase](selfbase-class-microsoft-lync-controls_1.md)  
                  Microsoft.Lync.Controls.MyPresenceChooser  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class MyPresenceChooser _
    Inherits SelfBase
'Usage
Dim instance As MyPresenceChooser
```

``` csharp
public class MyPresenceChooser : SelfBase
```

## Remarks

Use the MyPresenceChooser control in Microsoft Lync Control applications to display and change the user's current presence status selection. Clicking the control displays a list of presence status options, for example "Be Right Back". The user can change their presence status by selecting one of these options. The MyPresenceChooser control includes the ability to show and select custom presence states. This control can only be applied to the currently signed-in user and therefore does not have a [Source](contactbase-source-property-microsoft-lync-controls_1.md) property. Alternatively, the [MyStatusArea](mystatusarea-class-microsoft-lync-controls_1.md) provides similar functionality, integrated with other self-presence features such as the users name, photo, and editable personal note.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[MyPresenceChooser members](mypresencechooser-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

