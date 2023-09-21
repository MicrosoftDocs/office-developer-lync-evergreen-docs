---
title: Conversations (UCMA 4.0)
TOCTitle: Conversations
ms:assetid: cf285a40-d78a-4280-8760-4329e4ef7c86
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465985(v=office.15)
ms:contentKeyID: 57102794
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Conversations (UCMA 4.0)


**Applies to:** Lync 2013 | Lync Server 2013

A conversation is a concept that represents communication between a local participant and one or more remote participants, which can be either real people or applications. A conversation can be thought of as two-dimensional, with the number of media modalities representing one dimension, and the number of participants representing the other. In Microsoft Unified Communications Managed API 4.0 a conversation is represented by the [Conversation](https://msdn.microsoft.com/library/hh349224\(v=office.15\)) class.

A UCMA 4.0 application can initiate a conversation in either of the following modalities:

  - A single-mode Instant Message (IM) or audio conversation. (Other modes are possible, but require extending the UCMA 4.0 platform to work with calls that use different media types.)

  - A multimodal conversation.

A conversation is also distinguished by its number of participants: a conversation involving two parties is a two-party conversation. A conversation with three or more participants is called a multiparty conversation:

  - A two-party conversation is one that consists of a local participant and a single remote participant.

  - A multiparty conversation is one that consists of a local participant and two or more remote participants. An application can start a multiparty conversation directly, or can escalate a two-party conversation to a multi-party conversation (a conference).

The majority of conversations occur between two participants. To optimize such conversations so that they conserve server resources, these conversations are (by default) carried out with media travelling peer-to-peer along the best available path, while the signaling continues to be proxied by Microsoft Lync Server 2013.

## MCU-type conversations

A local endpoint associated with the conversation can have multiple calls with the same modality, provided that the value of the local endpoint’s [EndpointType](https://msdn.microsoft.com/library/hh380871\(v=office.15\)) property is **Conference**. Such a conversation is called an MCU (multi-point control unit)-type conversation. If the endpoint’s **EndpointType** property is any other value (**User**, **Application**, or **Gateway**), each media type present can be associated with only one call.

An MCU type conversation is a variation of multiparty conversation except for one main difference; an MCU type conversation can have multiple established calls with the same modality. Typically, an application uses a MCU-type conversation when it wants to build an MCU application.

## In this section

  - [Conversation state transitions - outbound](conversation-state-transitions-outbound.md)

  - [Conversation state transitions - inbound](conversation-state-transitions-inbound.md)

  - [Creating an outgoing two-party conversation](creating-an-outgoing-two-party-conversation.md)

  - [Impersonating a user](impersonating-a-user.md)

  - [Registering for conversation events](registering-for-conversation-events.md)

  - [Adding a modality to an existing conversation](adding-a-modality-to-an-existing-conversation.md)

  - [Escalating a two-party conversation to a conference](escalating-a-two-party-conversation-to-a-conference.md)

  - [Terminating a conversation](terminating-a-conversation.md)

