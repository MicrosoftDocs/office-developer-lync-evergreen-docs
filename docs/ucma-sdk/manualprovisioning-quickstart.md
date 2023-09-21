---
title: ManualProvisioning (QuickStart)
TOCTitle: ManualProvisioning (QuickStart)
ms:assetid: 092727ec-d2a6-4413-a55e-a85da522f2dd
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454830(v=office.15)
ms:contentKeyID: 57103725
ms.date: 07/25/2014
mtps_version: v=office.15
---

# ManualProvisioning (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

 

Sample name: ManualProvisioning

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\ManualProvisioning

## Description

In some situations, administrators might want to deploy Microsoft Unified Communications Managed API 4.0-based applications that are trusted by Microsoft Lync Server 2013, yet avoid installing a Central Management Store (CMS) replica on the server hosting the application. In these situations, the application must make use of manual provisioning.

In comparison to automatic provisioning, manual provisioning has several limitations. Specifically, manually-provisioned applications must be configured with a Globally Routable User Agent URI (GRUU), and trusted application endpoint owner URI and port, all of which must be configured in the CMS when the trusted application endpoint is configured. Additionally, it's usually necessary to configure manually-provisioned endpoints with the registrar FQDN and port. It's also necessary to determine the certificate the application will use if TLS transport is being employed. Additionally, changes to the trusted application endpoint owner properties will not be updated from CMS into the application.

For more information about provisioning trusted applications and endpoints in Microsoft Lync Server 2013, see [Activating a UCMA 4.0 trusted application](activating-a-ucma-4-0-trusted-application.md), as well as [General application activation](general-application-activation.md) and [Activating a manually-provisioned application](activating-a-manually-provisioned-application.md).

This sample demonstrates how to create a [CollaborationPlatform](https://msdn.microsoft.com/library/hh385176\(v=office.15\)) instance using the [ServerPlatformSettings](https://msdn.microsoft.com/library/hh382156\(v=office.15\)) constructor, establish a single [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)) instance, and monitor the state changes on the endpoint.

## Features

  - **CollaborationPlatform** creation from **ServerPlatformSettings**

  - **ApplicationEndpoint** establishment

  - Endpoint **StateChanged** notification handling

## Prerequisites

  - Microsoft Lync Server 2013.

  - Provisioned trusted **ApplicationEndpoint** instance.

## Running the sample

1.  Supply the configuration settings to be used by the sample in the accompanying App.config file, OR
    
    Supply these settings when prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

