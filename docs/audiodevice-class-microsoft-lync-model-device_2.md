---
title: AudioDevice class (Microsoft.Lync.Model.Device)
TOCTitle: AudioDevice class
ms:assetid: T:Microsoft.Lync.Model.Device.AudioDevice_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.device.audiodevice_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598498
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Device.AudioDevice
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AudioDevice class

Represents an audio device connected to a local computer.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWFull**  
        [Microsoft.Lync.Model.Device.Device](device-class-microsoft-lync-model-device_2.md)  
          Microsoft.Lync.Model.Device.AudioDevice  

**Namespace:**  [Microsoft.Lync.Model.Device](microsoft-lync-model-device-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class AudioDevice _
    Inherits Device
'Usage
Dim instance As AudioDevice
```

``` csharp
public class AudioDevice : Device
```

## Remarks

The Device.IsActive property returns true when the audio device will be used in the next conversation that is started. In addition, setting this property to true while a call is active causes this audio device to be used during the active call. After the call ends, the original audio device is used for future calls. In order to be sure the desired audio device is used for future calls, you must set the IsActive property to true when no calls are active.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[AudioDevice members](audiodevice-members-microsoft-lync-model-device_2.md)

[Microsoft.Lync.Model.Device namespace](microsoft-lync-model-device-namespace_2.md)

