---
title: Publication grammar, privacy, and interoperability
TOCTitle: Publication grammar, privacy, and interoperability
ms:assetid: d09a0e0c-21c4-47b3-a790-7a454af80596
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454682(v=office.15)
ms:contentKeyID: 57093212
ms.date: 02/11/2016
mtps_version: v=office.15
description: Learn Microsoft Lync Server 2013 Publication Grammar for Privacy & Interoperability. Enhance presence features & avoid conflicts.
---

# Publication grammar, privacy, and interoperability

Learn how to use a publication grammar in a Microsoft Lync Server 2013 deployment to ensure that specific publication rules are used.


**Applies to:** Lync 2013 | Lync Server 2013

In Lync Server 2013, presence publication, especially for remote presence watchers, is determined by the application logic of a client. When multiple types of clients operate independently, the publication rules of different clients may collide. To avoid such conflicts, a client can use a publication grammar to inform other clients of its publication logic and the other clients should follow the publication grammar to ensure that the same publication rules are adhered to.

A publication grammar is a set of rules that stipulates what category data should be published to a given set of containers and what membership scope a container can have. Publication grammars are stored on the server and provisioned to the client through the in-band provisioning process. However, the publication grammars are not enforced by the server. The client must follow the provisioned publication rules if it intends to interoperate with other presence applications.

There are two types of publications. One is called the open mode and the other the privacy mode. In an open-mode publication, a user has a set of category data published by default. In a privacy-mode publication, no category data is published by default and the user must explicitly set to have specified category instances published to specified containers.

An administrator of Lync Server 2013 sets a pool-wide policy specifying whether the open mode or the privacy mode is enabled. The client can receive this policy setting through the in-band provisioning.

In a Lync Server 2013 deployment, the default publication grammars are specified by Microsoft Lync 2013. To interoperate with Lync 2013, a presence application must follow the grammars and honor the specified publication rules.

## In this section

  - [Interoperating with Lync with publication grammars](interoperating-with-lync-with-publication-grammars.md)  
    Discusses how the publication grammar can be used to enable conflict-free interoperation with Microsoft Lync 2013 to leverage the well-tested presence features over a large install base.

  - [Publishing presence in privacy mode](publishing-presence-in-privacy-mode.md)  
    Discusses privacy mode presence publications and how a client can use presence policy and privacy publication grammar to enable it.

## See also

#### Concepts

[Get started with Enhanced Presence](get-started-with-enhanced-presence.md)

#### Other resources

[Lync Videos on Channel9](http://channel9.msdn.com/tags/lync)

