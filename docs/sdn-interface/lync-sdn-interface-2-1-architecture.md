---
title: Lync SDN Interface 2.1 architecture
TOCTitle: Lync SDN Interface 2.1 architecture
ms:assetid: c84231e4-5d96-4f1c-8747-a9a56d4794d9
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785192(v=office.15)
ms:contentKeyID: 62952677
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Lync SDN Interface 2.1 architecture

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

Conceptually, the Lync SDN Interface 2.1.1 consists of the following components:

- A Lync Dialog Listener (LDL) that captures signaling and quality observations about media traffic between Lync endpoints.

- A Lync SDN Manager (LSM) that collects the data from one or more LDLs and distributes to third-party network management systems.

- One or more network management systems, also known as network controllers, supporting a restful web service to receive and analyze the call and quality data posted from the LSM.

## Lync SDN Interface infrastructure

At a high level, the Lync SDN Interface 2.1.1 infrastructure consists of the Lync SDN Manager, the LDL/Lync Server FE and Network Controller, Lync clients, and one or more networks in the cloud.

**Figure 1. Lync SDN Interface architecture**

  
![Lync SDN Interface Architecture](images/Dn785192.Lync_sdn_interface_architecture_2(Office.15).png "Lync SDN Interface Architecture")

The types of Lync media traffic involving two or more Lync endpoints include audio and video calls and application-sharing.

The LDL is implemented as a Windows service, can work with both Lync Server 2010 and Lync Server 2013 as well as newer versions, and requires .NET Framework 3.5 or later versions. The LDL is configured to send data to the LSM.

The LSM is also a lightweight Windows service that might run on a separate virtual or hardware application server that uses Windows Server 2008 or later a later version (see [Deploying Lync SDN Interface 2.1.1](deploying-lync-sdn-interface-2-1-1.md)). The LSM is responsible for processing the dialog events received from the LDL component. It maintains state of the individual real-time streams—including whether the stream has started, ended, updated, and more—and sends the resulting XML data to the configured network management system. The LSM requires .NET Framework 4.5 or a later version. See the Lync SDN Manager Schema document (LyncSDNInterface.Schema.C.xsd) for development purposes.

Upon receiving a message, the LSM raises an event and invokes an event handler to parse the captured messages and to select those properties related to the quality of audio, video, and application sharing calls among Lync endpoints. The LSM then posts the data in an XML format to the registered network management systems and logs relevant events along the way.

A network management system runs independently of the LSM and its underlying Lync Server environment. This management system serves to monitor and analyze the network elements and traffic for the Lync clients, in addition to various other kinds of network traffic. It uses a web service to receive as input the Lync call and quality data captured by the LSM. The web service must be configured in the LSM so that it can post the Lync call and quality data to the configured web service address. In the Lync SDN Interface 2.1.1 Setup Wizard, the web service address is known as the SubmitUri.

When a Lync user calls another Lync user, a SIP dialog is established. SIP messages are exchanged between the client and Lync Server. Specific SIP messages contain data reflecting media-related information relevant for Lync SDN Interface 2.1.1 and are forwarded to the Lync SDN Manager (LSM). The LSM is then responsible for verifying, combining and packaging the call and quality data in XML and posting them to the configured web service of one or more network management systems. Figure 2 shows this process.

**Figure 2. Detailed Lync SDN Interface 2.1.1 architecture, with two Lync clients, a single Lync Server FE, an LSM, and a network controller**

![Architecture of Lync SDN Interface](images/Dn785192.architecture_lync_sdn_api(Office.15).png "Architecture of Lync SDN Interface")

## See also

- [Understanding Lync SDN Interface 2.1.1](understanding-lync-sdn-interface-2-1-1.md)
- [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

