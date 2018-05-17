---
title: ClientSettings.CanSetValue method  (Microsoft.Lync.Model)
TOCTitle: 'CanSetValue method '
ms:assetid: M:Microsoft.Lync.Model.ClientSettings.CanSetValue(Microsoft.Lync.Model.ClientSettingsType)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.clientsettings.cansetvalue(v=office.15)
ms:contentKeyID: 48596277
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ClientSettings.CanSetValue
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ClientSettings.CanSetValue method

test if the client setting can be set.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanSetValue ( _
    settingType As ClientSettingsType _
) As Boolean
'Usage
Dim instance As ClientSettings
Dim settingType As ClientSettingsType
Dim returnValue As Boolean

returnValue = instance.CanSetValue(settingType)
```

``` csharp
public bool CanSetValue(
    ClientSettingsType settingType
)
```

#### Parameters

  - settingType  
    Type: [Microsoft.Lync.Model.ClientSettingsType](clientsettingstype-enumeration-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## See also

#### Reference

[ClientSettings class](clientsettings-class-microsoft-lync-model_2.md)

[ClientSettings members](clientsettings-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

