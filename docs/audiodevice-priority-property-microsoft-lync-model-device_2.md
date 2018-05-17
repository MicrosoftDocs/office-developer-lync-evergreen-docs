---
title: AudioDevice.Priority property  (Microsoft.Lync.Model.Device)
TOCTitle: 'Priority property '
ms:assetid: P:Microsoft.Lync.Model.Device.AudioDevice.Priority_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.device.audiodevice.priority_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598604
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Device.AudioDevice.Priority
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AudioDevice.Priority property

Gets the priority of the audio device.

**Namespace:**  [Microsoft.Lync.Model.Device](microsoft-lync-model-device-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Priority As Integer
    Get
'Usage
Dim instance As AudioDevice
Dim value As Integer

value = instance.Priority
```

``` csharp
public int Priority { get; }
```

#### Property value

Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

## Remarks

The device priority reflects the capability of an audio device. A higher number indicates that the audio device has better capability than an audio device with a lower priority.

## See also

#### Reference

[AudioDevice class](audiodevice-class-microsoft-lync-model-device_2.md)

[AudioDevice members](audiodevice-members-microsoft-lync-model-device_2.md)

[Microsoft.Lync.Model.Device namespace](microsoft-lync-model-device-namespace_2.md)

