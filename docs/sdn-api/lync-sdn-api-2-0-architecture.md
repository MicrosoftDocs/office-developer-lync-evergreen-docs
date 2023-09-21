---
title: Lync SDN API 2.0 architecture
TOCTitle: Lync SDN API 2.0 architecture
ms:assetid: 60424a91-49db-4aed-9570-07eb94a4b5f7
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439293(v=office.15)
ms:contentKeyID: 57261029
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Lync SDN API 2.0 architecture

**Applies to:** Lync 2013 | Lync Server 2013

Conceptually, the Lync SDN API 2.0 consists of the following components:

- A Lync Dialog Listener (LDL) that captures signaling and diagnostic observations about media traffic between or among Lync endpoints.

- A Lync SDN Manager (LSM) that collects the data from one or more LDLs and distributes to third-party network management systems.

- One or more network management systems supporting a restful Web service to receive and analyze the diagnostic data posted from the LSM.

## Lync SDN API architecture

A graphical illustration of the Lync SDN API 2.0 is presented in Figure 1.

**Figure 1: Architecture of the Lync SDN API 2.0**

![Architecture of Lync SDN API](images/Dn439293.architecture_lync_sdn_api(Office.15).png "Architecture of Lync SDN API")

The types of Lync media traffic involving two or more Lync endpoints include audio and video calls, as well as application-sharing.

The LDL is implemented as a Windows service, can work with both Lync Server 2010 and Lync Server 2013, and requires .NET Framework 3.5 or higher. The LDL is configured to send data to the LSM.

The LSM is also a lightweight Windows Service that runs on a separate virtual or hardware application server with Windows Server 2008 or later. The LSM is responsible for processing the dialog events received from the LDL component. It maintains state of the individual real-time streams—including starting state, ending state, updated state, and more—and sends the resulting XML data to the configured network management system. Developers can utilize the new LSM XML schema for 2.0, due to its added and optimized enhancements. The LSM requires .NET Framework 4.5 or higher. Please see the Lync SDN Manager Schema document (.xsd) for development purposes. Also see the "Backwards Compatibility" section below for more info.

IT Pros should be aware that LSM for Lync SDN API 2.0 can be scaled out to have a secondary LSM in case of loss of primary. Switchover to the secondary is automatic, based on the LDL components’ experience with the configured primary LSM. The previous primary will become the new secondary, once the issues that caused it to stop receiving messages from the LDL are fixed. Optionally, if you want to change the order back to the original primary/secondary, you can restart the LDL. Note that in Lync SDN API 2.0, state is not shared between primary and secondary LSMs, and LSM will not send incomplete or out of sync messages to the network management system. The LDL configuration file has a place for primary (submituri) and secondary (alternativeuri).

Upon receiving a message, the LSM raises an event and invokes an event handler to parse the captured messages and to select those properties related to the quality of audio, video, and application sharing calls among Lync endpoints. The LSM then posts the data in an XML format to the registered network management systems and logs relevant events along the way.

LSM for Lync SDN API 2.0 can be configured to be compatible with the XML schema used in Lync SDN API 1.2. When in compatibility mode, LSM does not maintain state. New feature enhancements such as new message types, improved error reporting, linking error messages more efficiently to specific stream data, are not available. However, compliance to the new 2.0 XML schema is required for any LSM for Lync SDN API 2.0 enhancements.

A network management system runs independently of the LSM and its underlying Lync Server environment. This management system serves to monitor and analyze the Lync-dependent network elements and traffic for its contracted clients, in addition to various other types of network traffic. It uses a Web service to receive as input the Lync network diagnostic data captured by the LSM. The Web service must be registered with the LSM it so that can post the Lync network diagnostic data to the registered Web service address. In the Lync SDN API 2.0 Setup Wizard, the Web service address is known as the SubmitUri.

