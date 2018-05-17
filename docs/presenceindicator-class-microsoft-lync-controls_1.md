---
title: PresenceIndicator class (Microsoft.Lync.Controls)
TOCTitle: PresenceIndicator class
ms:assetid: T:Microsoft.Lync.Controls.PresenceIndicator_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.presenceindicator_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596304
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.PresenceIndicator
dev_langs:
- CSharp
- JScript
- VB
- other
---

# PresenceIndicator class

The PresenceIndicator control displays one of several icons that indicate the presence of a given user.

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
                  [Microsoft.Lync.Controls.AvailabilityIcon](availabilityicon-class-microsoft-lync-controls_1.md)  
                    Microsoft.Lync.Controls.PresenceIndicator  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class PresenceIndicator _
    Inherits AvailabilityIcon
'Usage
Dim instance As PresenceIndicator
```

``` csharp
public class PresenceIndicator : AvailabilityIcon
```

## Remarks

The PresenceIndicator control is a stand-alone control representing a single contact, and enables access to the quick connect menu and the contact card for the user. The control also can display a photo for the given user.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[PresenceIndicator members](presenceindicator-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

