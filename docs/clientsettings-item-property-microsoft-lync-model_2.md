---
title: ClientSettings.Item property  (Microsoft.Lync.Model)
TOCTitle: 'Item property '
ms:assetid: P:Microsoft.Lync.Model.ClientSettings.Item(Microsoft.Lync.Model.ClientSettingsType)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.clientsettings.item(v=office.15)
ms:contentKeyID: 48600256
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ClientSettings.Item
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ClientSettings.Item property

Update a client setting, an event will be raised when setting changed after this.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Default Property Item ( _
    _settingType As ClientSettingsType _
) As Object
    Get
    Set
'Usage
Dim instance As ClientSettings
Dim _settingType As ClientSettingsType
Dim value As Object

value = instance(_settingType)

instance(_settingType) = value
```

``` csharp
public Object this[
    ClientSettingsType _settingType
] { get; set; }
```

#### Parameters

  - \_settingType  
    Type: [Microsoft.Lync.Model.ClientSettingsType](clientsettingstype-enumeration-microsoft-lync-model_2.md)  

#### Property value

Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

## See also

#### Reference

[ClientSettings class](clientsettings-class-microsoft-lync-model_2.md)

[ClientSettings members](clientsettings-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

