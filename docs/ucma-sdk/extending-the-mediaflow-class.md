---
title: Extending the MediaFlow class
TOCTitle: Extending the MediaFlow class
ms:assetid: e6f88071-233c-43b2-b718-59a323bd039c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466106(v=office.15)
ms:contentKeyID: 57103353
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Extending the MediaFlow class


**Applies to:** Lync 2013 | Lync Server 2013

The [MediaFlow](https://msdn.microsoft.com/en-us/library/hh366262\(v=office.15\)) abstract class represents a generic flow concept for objects that send or receive media. A nonabstract subclass represents the flow of a specific media type. Microsoft Unified Communications Managed API 4.0 provides two **MediaFlow** subclasses: [AudioVideoFlow](https://msdn.microsoft.com/en-us/library/hh383533\(v=office.15\)) and [InstantMessagingFlow](https://msdn.microsoft.com/en-us/library/hh383312\(v=office.15\)). These classes represent flows whose media type is, respectively, audio/video and message.

A developer who intends to support a different media type must implement a **MediaFlow** subclass that represents that media type.

None of the methods, properties, and events on the abstract **MediaFlow** class are themselves abstract. As a result, a subclass that inherits from the **MediaFlow** class is not required to provide overriding method, property, or event definitions.

