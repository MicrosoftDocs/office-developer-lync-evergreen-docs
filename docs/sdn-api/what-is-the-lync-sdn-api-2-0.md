---
title: What is the Lync SDN API 2.0?
TOCTitle: What is the Lync SDN API 2.0?
ms:assetid: fba44310-0618-4662-8117-44c3b1ebe57b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439292(v=office.15)
ms:contentKeyID: 57261028
ms.date: 07/24/2014
mtps_version: v=office.15
---

# What is the Lync SDN API 2.0?


**Applies to:** Lync 2013 | Lync Server 2013

In any given Lync Server deployment, the Lync end-user experience can be adversely impacted by poor network performance, resulting in dropped calls or jittering audio. Network administrators can use a network management system and the Lync SDN API 2.0 to monitor traffic down to a single media stream in real-time and optimize the quality of service experiences with Lync.

## The Lync SDN API

The Lync SDN API 2.0 is designed to provide 3rd-party network management system developers with a programming interface to receive relevant Lync network diagnostic data including quality of experience data.

The Lync SDN API 2.0 is distributed as a downloadable installation package. This documentation explains how to install and configure the Lync SDN API 2.0 to work with one or more known network management systems. It also provides a technical reference to the Lync network diagnostic data. To provide a contextual framework for the technical information that follows, let’s take a look at the conceptual framework of the Lync SDN API 2.0.

## The Lync SDN API schema

In Lync SDN API 2.0, the diagnostic data is defined by the Lync SDN API Schema A. This schema presents an update from Lync SDN API Schema 1.0 as more data types are added and some improvements made to the version 1.0 elements. However, Lync SDN API 2.0 supports Lync SDN API Schema 1.0, provided that the backward compatible mode is enabled on Lync SDN API 2.0.

