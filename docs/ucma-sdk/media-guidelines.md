﻿---
title: Media guidelines
TOCTitle: Media guidelines
ms:assetid: 4c461569-1110-4cc4-aed1-f7f675b6bbc9
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466086(v=office.15)
ms:contentKeyID: 57103196
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Media guidelines


**Applies to:** Lync 2013 | Lync Server 2013

The following describes guidelines and tips for developers of applications that work with audio media:

  - The [Close()](https://msdn.microsoft.com/library/hh384406\(v=office.15\)) method on a [WmaFileSource](https://msdn.microsoft.com/library/hh381280\(v=office.15\)) object must be called after the application is finished with this object. If **Close** is not called, the underlying unmanaged object will not be disposed, causing a memory leak for the application.

  - Audio clipping can sometimes occur when an application plays media for a call between the application and a remote endpoint. To prevent this from occurring, the application should ensure that the value of the [State](https://msdn.microsoft.com/library/hh381151\(v=office.15\)) property on [AudioVideoCall](https://msdn.microsoft.com/library/hh383901\(v=office.15\)) is **Established** and that the value of the [State](https://msdn.microsoft.com/library/hh349893\(v=office.15\)) property on [AudioVideoFlow](https://msdn.microsoft.com/library/hh383533\(v=office.15\)) is **Active** before it starts the **Player**.

  - An application that plays a media file located on a network share should use **Buffered** mode (a value of the **MediaSourceBufferedMode** enumeration) with [BeginPrepareSource(MediaSourceOpenMode, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh349115\(v=office.15\)). Otherwise, if the network share is disconnected while a [Player](https://msdn.microsoft.com/library/hh349780\(v=office.15\)) object is playing the file, the engine thread that is handling the call will be blocked and the call will terminate due to a time-out. The time-out also disconnects any other calls within this engine thread.

  - An application that interoperates with endpoints that use this hold syntax—c=IN IP4 0.0.0.0—to perform a hold operation, should verify that the value of the [State](https://msdn.microsoft.com/library/hh349893\(v=office.15\)) property on the [AudioVideoFlow](https://msdn.microsoft.com/library/hh383533\(v=office.15\)) object is **Active**, and that the value of the [Enabled](https://msdn.microsoft.com/library/hh365886\(v=office.15\)) property on an **AudioChannel** instance is true prior to performing any recording operation.

  - An application that expects a remote endpoint to place a call on hold using this syntax—c=IN IP4 0.0.0.0—while recording audio, should ensure that the file length (the [Duration](https://msdn.microsoft.com/library/hh384378\(v=office.15\)) property on [WmaFileSource](https://msdn.microsoft.com/library/hh381280\(v=office.15\))) reflects the actual recorded audio length. To do so, the application should perform the following check in its handler for the [ConfigurationChanged](https://msdn.microsoft.com/library/hh385088\(v=office.15\)) event.
    
    Check the [Enabled](https://msdn.microsoft.com/library/hh365886\(v=office.15\)) property on the [AudioChannel](https://msdn.microsoft.com/library/hh349872\(v=office.15\)) instance.
    
      - If the value is false, pause the recorder by calling the [Pause()](https://msdn.microsoft.com/library/hh349541\(v=office.15\)) method on the [Recorder](https://msdn.microsoft.com/library/hh381624\(v=office.15\)) instance.
    
      - If the value is true, restart the recorder by calling the [Start()](https://msdn.microsoft.com/library/hh383534\(v=office.15\)) method on the **Recorder** instance.

  - An application that expects a remote endpoint to place a call on hold using this syntax—c=IN IP4 0.0.0.0—while playing audio, can either pause the audio while the call is on hold, or continue playing the audio while the call is on hold. To ensure that when the call resumes, the audio played to the remote endpoint starts at the correct position, an application should perform one of the following actions:
    
      - The application intends to pause the audio file while the call is on hold.
        
        In the handler for the [ConfigurationChanged](https://msdn.microsoft.com/library/hh385088\(v=office.15\)) event, the application should call the [Pause()](https://msdn.microsoft.com/library/hh381641\(v=office.15\)) method on the **Player** instance if the value of the [Enabled](https://msdn.microsoft.com/library/hh365886\(v=office.15\)) property on the [AudioChannel](https://msdn.microsoft.com/library/hh349872\(v=office.15\)) instance is false (call placed on hold). If the value of the **Enabled** property is true (call resumed), the application should call the [Start()](https://msdn.microsoft.com/library/hh382632\(v=office.15\)) method on the **Player** instance.
    
      - The application intends to continue playing the audio file while the call is on hold.
        
        In the handler for the [ConfigurationChanged](https://msdn.microsoft.com/library/hh385088\(v=office.15\)) event, the application should call the [Stop()](https://msdn.microsoft.com/library/hh350156\(v=office.15\)) method on the **Player** instance if the value of the [Enabled](https://msdn.microsoft.com/library/hh365886\(v=office.15\)) property is false (call placed on hold). If the value of the **Enabled** property is true (call resumed), the application should calculate the length of time the call was on hold (in milliseconds), and skip forward in the audio file, using the [Skip(Int32)](https://msdn.microsoft.com/library/hh383920\(v=office.15\)) method on the **Player** instance.

