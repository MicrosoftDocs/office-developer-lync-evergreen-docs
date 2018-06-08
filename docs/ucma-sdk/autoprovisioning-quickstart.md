---
title: Autoprovisioning (QuickStart)
TOCTitle: Autoprovisioning (QuickStart)
ms:assetid: 1d165a95-177b-4710-bdd7-ee20292e1f9c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466139(v=office.15)
ms:contentKeyID: 57103462
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Autoprovisioning (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013



Sample name: AutoProvisioning

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\AutoProvisioning

## Description

Based on the ApplicationID specified, the sample initializes the collaboration platform and the application endpoint corresponding to the provisioned application. The sample will establish as many **ApplicationEndpoint** instances as have been provisioned on the particular trusted application within the Microsoft Lync Server 2013 deployment. For more information about provisioning trusted applications and endpoints in Lync Server 2013, see [Activating a UCMA 4.0 trusted application](activating-a-ucma-4-0-trusted-application.md), as well as [General application activation](general-application-activation.md) and [Activating a manually-provisioned application](activating-a-manually-provisioned-application.md).

Throughout the lifetime of the process, the sample application listens for **StateChanged** and **ProvisioningDataChanged** notifications on the application endpoint and reflects these notifications in the console. Developers can modify the provisioning information relevant to ApplicationEndpoints used in this sample (for example, by updating contact object properties such as displayName) to see how the **ProvisioningData** changes are surfaced.

## Features

  - **ApplicationEndpointSettings** creation using **RegisterForApplicationEndpointSettings**

  - **ApplicationEndpoint** establishment

  - Endpoint **StateChanged** notification handling

  - **ProvisioningDataChanged** notification handling

## Prerequisites

  - Microsoft Lync Server 2013.

  - Provisioned trusted application endpoint

## Running the sample

1.  Supply the provisioned Application ID to be used by the sample in the accompanying app.config file, OR
    
    Supply this value when prompted for it when you run the sample.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

