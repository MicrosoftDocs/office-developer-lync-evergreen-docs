---
title: Receiving in-band provisioning data
TOCTitle: Receiving in-band provisioning data
ms:assetid: a05215d3-f7ab-45d1-8452-2410640d2b5c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454636(v=office.15)
ms:contentKeyID: 57092878
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Receiving in-band provisioning data


_**Applies to:** Lync 2013 | Lync Server 2013_

The enhanced presence publication and subscription infrastructure is also used to roam configuration data through in-band provisioning. The data includes server configuration, location profile, various policies, as well as user settings. It is stored on the server but is needed by a client at various stages in an application.

At the protocol level, receiving the provisioning data involves submitting a SUBSCRIBE request whose payload contains names of specified provisioning groups. The results are returned as the provisioning groups that contain the specified provisioning data.

Microsoft Unified Communications Managed API 4.0 exposes in-band provisioning data through various API objects. This section discusses how some of the in-band provisioning data can be processed by using UCMA.

In UCMA 4.0, the provisioning data are encapsulated by a LocalEndpoint object. You can obtain the publication grammars by reading the ContainerManifest and CategoryPublicationManifest properties on the LocalOwnerPresence instance of the established endpoint.

``` csharp
    LocalEndpoint endpoint = …;

    string cpm = localEndpoint.LocalOwnerPresence.CategoryPublicationManifest;
    string cm = localEndpoint.LocalOwnerPresence.ContainerManifest;
```

You can receive the cached values of the other provisioning data by calling the GetProvisioningData method on the LocalEndpoint instance.

``` csharp
    ProvisionData provData = endpoint.GetProvisioningData();
```

To query the latest provisioning data on the server, make an asynchronous call to BeginGetProvisioningData/EndGetProvisioningData.

``` csharp
    localEndpoint.EndGetProvisioningData(localEndpoint.BeginGetProvisioningData(null, null));
```

## In this section

  - 

  - [Parsing endpoint configuration](parsing-endpoint-configuration.md)  

  - [Parsing location policy](parsing-location-policy.md)

  - [Parsing location profile](parsing-location-profile.md)

  - [Parsing media configuration](parsing-media-configuration.md)

  - [Parsing meeting policy](parsing-meeting-policy.md)

  - [Parsing mobility policy](parsing-mobility-policy.md)

  - [Parsing server configuration](parsing-server-configuration.md)

  - [Parsing unified communications policy](parsing-unified-communications-policy.md)

  - [Parsing user settings](parsing-user-settings.md)

## See also

#### Concepts

[General features of Enhanced Presence](general-features-of-enhanced-presence.md)

