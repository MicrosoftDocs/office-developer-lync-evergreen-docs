---
title: StartAudioCallButton class (Microsoft.Lync.Controls)
TOCTitle: StartAudioCallButton class
ms:assetid: T:Microsoft.Lync.Controls.StartAudioCallButton_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.startaudiocallbutton_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48588575
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.StartAudioCallButton
dev_langs:
- CSharp
- JScript
- VB
- other
---

# StartAudioCallButton class

Use the StartAudioCallButton control in Lync Control applications to enable the user to open a Lync conversation window and start a voice conversation between the user who activated the control, and another user.

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
                    Microsoft.Lync.Controls.StartAudioCallButton  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class StartAudioCallButton _
    Inherits ContactButton
'Usage
Dim instance As StartAudioCallButton
```

``` csharp
public class StartAudioCallButton : ContactButton
```

## Remarks

StartAudioCallButton is a split-button control. When clicked, the left side of the split button places a call to the default number associated with the contact. The right side of the control exposes a menu of calling options, such as Lync Call, Work, and Voice Mail.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[StartAudioCallButton members](startaudiocallbutton-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

