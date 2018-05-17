---
title: DeviceManager.ActiveAudioDevice property  (Microsoft.Lync.Model.Device)
TOCTitle: 'ActiveAudioDevice property '
ms:assetid: P:Microsoft.Lync.Model.Device.DeviceManager.ActiveAudioDevice_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.device.devicemanager.activeaudiodevice_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590583
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Device.DeviceManager.ActiveAudioDevice
dev_langs:
- CSharp
- JScript
- VB
- other
---

# DeviceManager.ActiveAudioDevice property

Gets and sets the active audio device.

**Namespace:**  [Microsoft.Lync.Model.Device](microsoft-lync-model-device-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Property ActiveAudioDevice As AudioDevice
    Get
    Set
'Usage
Dim instance As DeviceManager
Dim value As AudioDevice

value = instance.ActiveAudioDevice

instance.ActiveAudioDevice = value
```

``` csharp
public AudioDevice ActiveAudioDevice { get; set; }
```

#### Property value

Type: [Microsoft.Lync.Model.Device.AudioDevice](audiodevice-class-microsoft-lync-model-device_2.md)  

## Remarks

If a conversation is going on, then setting this changes the currently in used device to the new device. This change happens in mid call and is not remembered when that conversation ends. If a conversation is not going on, then setting this property changes default device so the set device will be used any time a new conversation starts. Please note that when you change the active audio device between calls, the device you set is not persisted after you close the Lync client. To persist an audio device, you must set the audio device in the Lync client options Audio Device Settings page.

## See also

#### Reference

[DeviceManager class](devicemanager-class-microsoft-lync-model-device_2.md)

[DeviceManager members](devicemanager-members-microsoft-lync-model-device_2.md)

[Microsoft.Lync.Model.Device namespace](microsoft-lync-model-device-namespace_2.md)

