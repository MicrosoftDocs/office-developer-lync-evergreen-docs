---
title: MyNoteBox class (Microsoft.Lync.Controls)
TOCTitle: MyNoteBox class
ms:assetid: T:Microsoft.Lync.Controls.MyNoteBox_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.mynotebox_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597156
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.MyNoteBox
dev_langs:
- CSharp
- JScript
- VB
- other
---

# MyNoteBox class

Use the MyNoteBox control in Lync Control applications to display and change the current user's personal note.

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
                  Microsoft.Lync.Controls.MyNoteBox  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "PART_NoteEditTextBox", Type := GetType(TextBox))> _
<TemplatePartAttribute(Name := "PART_EditNoteToggleButton", Type := GetType(ToggleButton))> _
Public Class MyNoteBox _
    Inherits SelfBase
'Usage
Dim instance As MyNoteBox
```

``` csharp
[TemplatePartAttribute(Name = "PART_NoteEditTextBox", Type = typeof(TextBox))]
[TemplatePartAttribute(Name = "PART_EditNoteToggleButton", Type = typeof(ToggleButton))]
public class MyNoteBox : SelfBase
```

## Remarks

The user can change their personal note by typing in new text and pressing the Enter key.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[MyNoteBox members](mynotebox-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

