---
title: ClientSettings.SettingChanged event (Microsoft.Lync.Model)
TOCTitle: SettingChanged event
ms:assetid: E:Microsoft.Lync.Model.ClientSettings.SettingChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.clientsettings.settingchanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591194
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ClientSettings.SettingChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ClientSettings.SettingChanged event

Raised when a client setting is changed.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event SettingChanged As EventHandler(Of ClientSettingsChangedEventArgs)
'Usage
Dim instance As ClientSettings
Dim handler As EventHandler(Of ClientSettingsChangedEventArgs)

AddHandler instance.SettingChanged, handler
```

``` csharp
public event EventHandler<ClientSettingsChangedEventArgs> SettingChanged
```

## See also

#### Reference

[ClientSettings class](clientsettings-class-microsoft-lync-model_2.md)

[ClientSettings members](clientsettings-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

