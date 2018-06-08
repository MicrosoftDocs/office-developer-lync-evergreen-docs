---
title: Understanding Lync SDN Interface 2.1.1
TOCTitle: Understanding Lync SDN Interface 2.1.1
ms:assetid: 4c97bce1-4b8b-4c13-8ec6-99eed59d88fc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785193(v=office.15)
ms:contentKeyID: 62952675
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Understanding Lync SDN Interface 2.1.1


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

**In this article**  
The Lync SDN Interface  
The Lync SDN Interface schema  
In this section  
Additional resources  

In any given Lync Server deployment, poor network performance can adversely affect the Lync end user experience. This results in dropped calls or jittering audio. Network administrators can use a network management system and the Lync SDN Interface 2.1.1 to monitor traffic down to a single media stream in real time and optimize the quality of service experiences with Lync.

## The Lync SDN Interface

The Lync SDN Interface 2.1.1 provides third-party network management system developers with an interface to receive relevant Lync call and quality data.

The Lync SDN Interface 2.1.1 is distributed as a downloadable installation package. This content explains how to install and configure the Lync SDN Interface 2.1.1 to work with one or more known network management systems. It also provides a technical reference to the Lync call and quality data provided. To get a contextual framework for the technical information, take a look at the conceptual framework of the Lync SDN Interface 2.1.1.


> [!IMPORTANT]
> <P>The Lync SDN Interface 2.1.1 version is primarily a bug fix release; its message format and semantics are fully compatible with Lync SDN 2.1</P>



## The Lync SDN Interface schema

In Lync SDN Interface 2.1.1, the call and quality data is defined by the Lync SDN Interface Schema C. Documentation of the schema can be found in [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md). The source file of the schema is **LyncSDNInterface.Schema.C.xsd**. This schema presents an update from **Lync SDN API Schema A**, which was used in Lync SDN API 2.0. More data types are added and some improvements have been introduced. However, it does not offer backward compatibility with the previous versions.


> [!NOTE]
> <P>For version 2.1.1, the schema file has been reformatted and updated with additional documentation to support use of metrics; furthermore, some fields have been marked "obsolete."</P>



## In this section

  - [Using the Lync SDN Interface 2.1](using-the-lync-sdn-interface-2-1.md)

  - [Lync SDN Interface 2.1 architecture](lync-sdn-interface-2-1-architecture.md)

  - [Deploying Lync SDN Interface 2.1.1](deploying-lync-sdn-interface-2-1-1.md)

  - [Enhanced features of Lync SDN Interface 2.1.1](enhanced-features-of-lync-sdn-interface-2-1-1.md)

  - [In-call QoE algorithm and throttling](in-call-qoe-algorithm-and-throttling.md)

## See also

  - [Overview of Lync SDN Interface 2.1.1](overview-of-lync-sdn-interface-2-1-1.md)

  - [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

