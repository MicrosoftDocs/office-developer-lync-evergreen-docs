---
title: StartInstantMessagingButton class (Microsoft.Lync.Controls)
TOCTitle: StartInstantMessagingButton class
ms:assetid: T:Microsoft.Lync.Controls.StartInstantMessagingButton_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.startinstantmessagingbutton_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48593928
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.StartInstantMessagingButton
dev_langs:
- CSharp
- JScript
- VB
- other
---

# StartInstantMessagingButton class

Use the StartInstantMessagingButton control in Lync Control applications to enable the user to open a Lync conversation window and start an instant messaging conversation between the user who activated the control, and another user specified by the [Source](contactbase-source-property-microsoft-lync-controls_1.md) property.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [Microsoft.Lync.Controls.UCBase](ucbase-class-microsoft-lync-controls_1.md)  
                [Microsoft.Lync.Controls.ContactBase](contactbase-class-microsoft-lync-controls_1.md)  
                  [Microsoft.Lync.Controls.ContactButton](contactbutton-class-microsoft-lync-controls_1.md)  
                    Microsoft.Lync.Controls.StartInstantMessagingButton  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class StartInstantMessagingButton _
    Inherits ContactButton
'Usage
Dim instance As StartInstantMessagingButton
```

``` csharp
public class StartInstantMessagingButton : ContactButton
```

## Remarks

The control can also start an IM conversation with a distribution group.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[StartInstantMessagingButton members](startinstantmessagingbutton-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

