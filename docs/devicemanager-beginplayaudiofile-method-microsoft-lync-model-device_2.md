---
title: DeviceManager.BeginPlayAudioFile method  (Microsoft.Lync.Model.Device)
TOCTitle: 'BeginPlayAudioFile method '
ms:assetid: M:Microsoft.Lync.Model.Device.DeviceManager.BeginPlayAudioFile(System.String,Microsoft.Lync.Model.Device.AudioPlayBackModes,System.Boolean,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.device.devicemanager.beginplayaudiofile(v=office.15)
ms:contentKeyID: 48589266
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Device.DeviceManager.BeginPlayAudioFile
dev_langs:
- CSharp
- JScript
- VB
- other
---

# DeviceManager.BeginPlayAudioFile method

Plays audio file.

**Namespace:**  [Microsoft.Lync.Model.Device](microsoft-lync-model-device-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginPlayAudioFile ( _
    audioFileName As String, _
    playbackDevices As AudioPlayBackModes, _
    loop As Boolean, _
    deviceManagerCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As DeviceManager
Dim audioFileName As String
Dim playbackDevices As AudioPlayBackModes
Dim loop As Boolean
Dim deviceManagerCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginPlayAudioFile(audioFileName, _
    playbackDevices, loop, deviceManagerCallback, _
    state)
```

``` csharp
public IAsyncResult BeginPlayAudioFile(
    string audioFileName,
    AudioPlayBackModes playbackDevices,
    bool loop,
    AsyncCallback deviceManagerCallback,
    Object state
)
```

#### Parameters

  - audioFileName  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - playbackDevices  
    Type: [Microsoft.Lync.Model.Device.AudioPlayBackModes](audioplaybackmodes-enumeration-microsoft-lync-model-device_2.md)  

<!-- end list -->

  - loop  
    Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

<!-- end list -->

  - deviceManagerCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[DeviceManager class](devicemanager-class-microsoft-lync-model-device_2.md)

[DeviceManager members](devicemanager-members-microsoft-lync-model-device_2.md)

[Microsoft.Lync.Model.Device namespace](microsoft-lync-model-device-namespace_2.md)

