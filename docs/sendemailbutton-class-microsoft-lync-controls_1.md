---
title: SendEmailButton class (Microsoft.Lync.Controls)
TOCTitle: SendEmailButton class
ms:assetid: T:Microsoft.Lync.Controls.SendEmailButton_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.sendemailbutton_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597702
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.SendEmailButton
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SendEmailButton class

Use the SendEmailButton control in Lync Control applications to launch the user's preferred email program and compose an email to a selected contact.

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
                    Microsoft.Lync.Controls.SendEmailButton  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class SendEmailButton _
    Inherits ContactButton
'Usage
Dim instance As SendEmailButton
```

``` csharp
public class SendEmailButton : ContactButton
```

## Remarks

The selected contact must have an email address exposed in order for this feature to work. Optionally, you can specify a subject for the email as well. The control is designed to mimic the functionality provided by the corresponding button on the Quick Connect toolbar of the ContactCard. As such, it must be bound to a contact using the [Source](contactbase-source-property-microsoft-lync-controls_1.md) property before it can be used. When clicked, it launches the Microsoft Outlook dialog to initiate the desired action with that contact. This button is not a general purpose Outlook Integration tool. It is intended to be used together with other Lync Controls to provide a full set of collaboration options for interacting with a specific contact or distribution group. Despite the fact that no Lync functionality is actually used here, this control leverages the binding model of the other Lync Controls to provide the full scope of features accessible on the ContactCard quick-connect toolbar.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[SendEmailButton members](sendemailbutton-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

