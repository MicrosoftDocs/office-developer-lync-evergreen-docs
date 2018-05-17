---
title: PresenceIndicatorAutomationPeer.GetBoundingRectangleCore method  (Microsoft.Lync.Controls.AutomationPeers)
TOCTitle: 'GetBoundingRectangleCore method '
ms:assetid: M:Microsoft.Lync.Controls.AutomationPeers.PresenceIndicatorAutomationPeer.GetBoundingRectangleCore_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.automationpeers.presenceindicatorautomationpeer.getboundingrectanglecore_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600335
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.AutomationPeers.PresenceIndicatorAutomationPeer.GetBoundingRectangleCore
dev_langs:
- CSharp
- JScript
- VB
- other
---

# PresenceIndicatorAutomationPeer.GetBoundingRectangleCore method

Override **\[GetBoundingRectangleCore\]** to return the indicator's position and size

**Namespace:**  [Microsoft.Lync.Controls.AutomationPeers](microsoft-lync-controls-automationpeers-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overrides Function GetBoundingRectangleCore As Rect
'Usage
Dim returnValue As Rect

returnValue = Me.GetBoundingRectangleCore()
```

``` csharp
protected override Rect GetBoundingRectangleCore()
```

#### Return value

Type: [System.Windows.Rect](http://msdn2.microsoft.com/en-us/library/ms589713)  

## Remarks

In Silverlight, Viewbox does not allow for an automation client to find the size of it's underlying contents, so we manually do the computation and expose it through the override. In WPF, we can rely on FrameworkElement's implementation of **\[GetBoundingRectangleCore\]**

## See also

#### Reference

[PresenceIndicatorAutomationPeer class](presenceindicatorautomationpeer-class-microsoft-lync-controls-automationpeers_1.md)

[PresenceIndicatorAutomationPeer members](presenceindicatorautomationpeer-members-microsoft-lync-controls-automationpeers_1.md)

[Microsoft.Lync.Controls.AutomationPeers namespace](microsoft-lync-controls-automationpeers-namespace_1.md)

