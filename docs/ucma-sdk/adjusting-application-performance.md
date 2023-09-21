---
title: Adjusting application performance
TOCTitle: Adjusting application performance
ms:assetid: cad3fdf3-04b0-4db0-9ef9-bf5e7929e87f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466096(v=office.15)
ms:contentKeyID: 57103234
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Adjusting application performance


**Applies to:** Lync 2013 | Lync Server 2013

Because codecs have varying performance characteristics, UCMA 4.0 SDK exposes the UseHighPerformance property, which enables developers to choose between better server performance or better audio quality for their applications. **UseHighPerformance** is a property on the AudioChannelTemplate class in the Microsoft.Rtc.Collaboration.AudioVideo namespace.

Setting the **UseHighPerformance** property to true causes the UCMA 4.0 SDK platform to exclude lower-performance audio codes such as RTAudio-WB and RTAudio-NB. Setting the property to false causes the platform to include lower-performance audio codecs such as RTAudio-WB or RTAudio-NB.

Performance gain comes from reducing the time spent encoding and decoding audio, of which the more time-expensive operation is encoding. Encoding is particularly expensive with RTAudio. The **UseHighPerformance** setting limits the choice of codecs to those that can more quickly encode and decode audio packets.

## Using the UseHighPerformance property

For UCMA 4.0 SDK applications that require optimal server performance and scalability, set the **UseHighPerformance** property to true.

The following code shows a handler for the **AudioVideoFlowConfigurationRequested** event on an **AudioVideoCall** instance. The handler can be used for incoming and outgoing audio/video calls. In this code example, the **UseHighPerformance** property is set to true, thereby selecting server performance over audio quality.

```csharp
private void UserAvCall_AudioVideoFlowConfigurationRequested(object sender, AudioVideoFlowConfigurationRequestedEventArgs e)
{
  AudioVideoCall call = sender as AudioVideoCall;
  AudioVideoFlowTemplate template = new AudioVideoFlowTemplate(call.Flow);

  // Set High Performance
  template.Audio.Channels[ChannelLabel.AudioMono].UseHighPerformance = true;
  call.Flow.Initialize(template);
}
```

