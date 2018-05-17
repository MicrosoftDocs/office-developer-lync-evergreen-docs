---
title: MyStatusArea class (Microsoft.Lync.Controls)
TOCTitle: MyStatusArea class
ms:assetid: T:Microsoft.Lync.Controls.MyStatusArea_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.mystatusarea_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595813
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.MyStatusArea
dev_langs:
- CSharp
- JScript
- VB
- other
---

# MyStatusArea class

The MyStatusArea control displays the note string, an availability icon/photo, a textblock with the user's name, and a textblock with the user's location.

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
                  Microsoft.Lync.Controls.MyStatusArea  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplateVisualStateAttribute(Name := "PhotoLarge", GroupName := "PhotoModeStates")> _
<TemplateVisualStateAttribute(Name := "PhotoSmall", GroupName := "PhotoModeStates")> _
<TemplateVisualStateAttribute(Name := "PhotoHidden", GroupName := "PhotoModeStates")> _
Public Class MyStatusArea _
    Inherits SelfBase
'Usage
Dim instance As MyStatusArea
```

``` csharp
[TemplateVisualStateAttribute(Name = "PhotoLarge", GroupName = "PhotoModeStates")]
[TemplateVisualStateAttribute(Name = "PhotoSmall", GroupName = "PhotoModeStates")]
[TemplateVisualStateAttribute(Name = "PhotoHidden", GroupName = "PhotoModeStates")]
public class MyStatusArea : SelfBase
```

## Remarks

The MyStatusArea control also displays the MyStatusArea and MyPresenceChooser controls together. To display these in separate locations, use MyNoteBox and MyPresenceChooser as separate controls. Clicking the presence status box displays a list of presence options, for example "Be Right Back". The user can change their presence by selecting one of these. The user can change their note string by typing in new text and pressing the Enter key. Separately, the [MyPresenceChooser](mypresencechooser-class-microsoft-lync-controls_1.md) and [MyNoteBox](mynotebox-class-microsoft-lync-controls_1.md) controls provide similar functionality, for applications where a customized layout is necessary.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[MyStatusArea members](mystatusarea-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

