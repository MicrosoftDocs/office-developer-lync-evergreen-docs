---
title: PublishAlwaysOnline (QuickStart)
TOCTitle: PublishAlwaysOnline (QuickStart)
ms:assetid: cf7992a1-db45-417d-b0bc-b4e896779c8c
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454833(v=office.15)
ms:contentKeyID: 57103766
ms.date: 07/25/2014
mtps_version: v=office.15
---

# PublishAlwaysOnline (QuickStart)

**Applies to:** Lync 2013 | Lync Server 2013

**Sample name**: PublishAlwaysOnline

**Sample location**: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\PublishAlwaysOnline

## Description

Based on the Application ID specified, the sample initializes the platform and any trusted application endpoints corresponding to the provisioned application. Upon establishment, the endpoints publish a static presence of "alwaysonline" by setting the [AutomaticPresencePublicationEnabled](https://msdn.microsoft.com/library/hh381653\(v=office.15\)) property on an [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) object to true. The sample establishes as many application endpoints as have been provisioned on the particular trusted application within the Microsoft Lync Server 2013 deployment.

For more information about provisioning trusted applications and endpoints in Microsoft Lync Server 2013, see [Activating a UCMA 4.0 trusted application](activating-a-ucma-4-0-trusted-application.md) as well as [General application activation](general-application-activation.md) and [Activating a manually-provisioned application](activating-a-manually-provisioned-application.md).

Throughout the lifetime of the process, the sample application listens for the **StateChanged** event on the application endpoint and reflects the endpoint state changes in the console.

## Features

- Custom presence publication

- **ApplicationEndpoint** establishment

- **ApplicationEndpointSettings** creation by registering a delegate with **RegisterForApplicationEndpointSettings**

- Endpoint state change notification handling

## Prerequisites

- Lync Server 2013

- Provisioned trusted application endpoint

## Run the sample

1.  Supply the user credentials in the accompanying app.config file, or you'll be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio development system, and then press F5.

