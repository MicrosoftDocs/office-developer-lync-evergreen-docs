---
title: UCTreeViewItemAutomationPeer.ISelectionItemProvider.SelectionContainer property  (Microsoft.Lync.Controls.AutomationPeers)
TOCTitle: 'ISelectionItemProvider.SelectionContainer property '
ms:assetid: P:Microsoft.Lync.Controls.AutomationPeers.UCTreeViewItemAutomationPeer.System#Windows#Automation#Provider#ISelectionItemProvider#SelectionContainer_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Hh345715(v=office.15)
ms:contentKeyID: 48592363
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.AutomationPeers.UCTreeViewItemAutomationPeer.ISelectionItemProvider.SelectionContainer
dev_langs:
- CSharp
- JScript
- VB
- other
---

# UCTreeViewItemAutomationPeer.ISelectionItemProvider.SelectionContainer property

Gets the UI automation provider that implements [ISelectionProvider](http://msdn2.microsoft.com/en-us/library/ms608335) and acts as the container for the calling object.

**Namespace:**  [Microsoft.Lync.Controls.AutomationPeers](microsoft-lync-controls-automationpeers-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Private ReadOnly Property SelectionContainer As IRawElementProviderSimple
    Implements ISelectionItemProvider.SelectionContainer
    Get
'Usage
Dim instance As UCTreeViewItemAutomationPeer
Dim value As IRawElementProviderSimple

value = CType(instance, ISelectionItemProvider).SelectionContainer
```

``` csharp
IRawElementProviderSimpleISelectionItemProvider.SelectionContainer { get; }
```

#### Property value

Type: [System.Windows.Automation.Provider.IRawElementProviderSimple](http://msdn2.microsoft.com/en-us/library/ms608319)  
The UI automation provider.  

#### Implements

[ISelectionItemProvider.SelectionContainer](http://msdn2.microsoft.com/en-us/library/ms604383)  

## Remarks

This API supports the .NET Framework infrastructure and is not intended to be used directly from your code.

## See also

#### Reference

[UCTreeViewItemAutomationPeer class](uctreeviewitemautomationpeer-class-microsoft-lync-controls-automationpeers_1.md)

[UCTreeViewItemAutomationPeer members](uctreeviewitemautomationpeer-members-microsoft-lync-controls-automationpeers_1.md)

[Microsoft.Lync.Controls.AutomationPeers namespace](microsoft-lync-controls-automationpeers-namespace_1.md)

