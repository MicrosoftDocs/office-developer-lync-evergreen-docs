﻿---
title: Client platforms
TOCTitle: Client platforms
ms:assetid: 10b3cb99-b1ab-4a21-97e4-b6106781b25b
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466052(v=office.15)
ms:contentKeyID: 57103045
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Client platforms


**Applies to:** Lync 2013 | Lync Server 2013

When a [CollaborationPlatform](https://msdn.microsoft.com/library/hh385176\(v=office.15\)) instance is created, it can be created as a client platform, a server platform, or as a provisioned application server platform. Each of the three **CollaborationPlatform** constructors can be used to create one type of platform.

A client platform typically is used to support the creation of a large number of clients that can be used to simulate users connected to an application, for the purpose of carrying out stress and scalability testing on an implementation of an application server.

## Client platform characteristics

A client platform:

  - Uses a dedicated connection for each endpoint. This connection is used for all incoming and outgoing traffic on the endpoint.

  - Uses keep-alive messages over each connection for prompt detection of connection failures.

  - Does not establish trust with the server. Each endpoint must authenticate itself with the server using credentials for one of the supported authentication protocols.

  - Has a more limited set of media ports available as defined through in-band provisioning data. Even though a large number of endpoints can be created from a client platform, the number of simultaneous audio/video calls possible is low, by default.

A client platform can be used with a small number of user endpoints to test the functionality of an application to develop a custom desktop application that cannot be developed using Microsoft Unified Communications Client API or Microsoft Lync 2013 API. A client platform can also be used with a large number of user endpoints, using IM and Presence only (no audio or application sharing). A limited port range does not affect IM and Presence.

## Client platform usage examples

The following examples show how to initialize and uninitialize a client platform.

```csharp
private void Initialize()
{

  myPlatform = new CollaborationPlatform(new ClientPlatformSettings(userAgent, SipTransportType.Tls));
  myPlatform.BeginStartup(this.PlatformStartupCompleted, myPlatform);
  needCleanup = false;
}
```

    private void Uninitialize()
    {
      // Other clean-up operations...
    
      if (myPlatform != null)
      {
        myPlatform.BeginShutdown(this.PlatformShutdownCompleted, myPlatform));
      }
    }

The following examples are callback methods that are used by the methods in the preceding examples.

    private void PlatformStartupCompleted(IAsyncResult asyncResult) 
    {
      bool needCleanup = true;
      try
      {
        CollaborationPlatform platform = asyncResult.AsyncState as CollaborationPlatform;
        platform.EndStartup(asyncResult);
        needCleanup = false; 
        // Platform successfully started. Proceed with next steps.
      }
      catch (RealTimeException) 
      { 
        // Handle RealTime exception. 
      }
      finally
      { 
        if(needCleanup) 
        {
          // Handle cleanup.
        }
      }
    }
    
    private void PlatformShutdownCompleted(IAsyncResult asyncResult) 
    {
      CollaborationPlatform platform = asyncResult.AsyncState as CollaborationPlatform;
      platform.EndShutdown(asyncResult); 
      // EndShutdown will not throw RealTimeException or any subclass.
    }

