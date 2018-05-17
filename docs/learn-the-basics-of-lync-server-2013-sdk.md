---
title: Learn the basics of Lync Server 2013 SDK
TOCTitle: Learn the basics
ms:assetid: cc707782-84a8-461e-a776-952a4347e2e9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439063(v=office.15)
ms:contentKeyID: 57096313
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Learn the basics of Lync Server 2013 SDK

Learn how to use the Microsoft Lync Server 2013 SIP Application API to develop SIP applications that run on Microsoft Lync Server 2013.


_**Applies to:** Lync Server 2013_

The SIP applications can behave only as proxies or user agent servers (UAS) in the current version of the Microsoft Lync Server 2013 SIP Application Managed API. As a proxy, the Lync Server 2013 SIP Application API application serves to forward a processed SIP message to the next host or recipient.

The API supports two ways to handle and proxy a SIP message. The simplest way to handle and proxy a message involves using an application manifest and setting the value of the [proxyByDefault Element (Updated)](https://msdn.microsoft.com/en-us/library/hh364691\(v=office.15\)) element to true. This amounts to creating a script-only Lync Server 2013 SIP Application API application. The more advanced approach involves using the [Microsoft.Rtc.Sip](https://msdn.microsoft.com/en-us/library/jj266253\(v=office.15\)) namespace to process messages and manage transactions. This corresponds to a managed Lync Server 2013 SIP Application API application.

The Lync Server 2013 SIP Application API documentation discusses application manifests and includes information about script-based and managed code-based application components.

All applications require an application manifest, regardless of whether they implement any managed components.

## In this section

  - [SIP application manifest](sip-application-manifest.md)

  - [Microsoft SIP Processing language Script (Lync Server 2013 Preview SDK)](microsoft-sip-processing-language-script-lync-server-2013-preview-sdk.md)

  - [Managed SIP Application API](managed-sip-application-api.md)

## See also

#### Concepts

[Lync Server 2013 API references](https://msdn.microsoft.com/en-us/library/dn454963\(v=office.15\))

#### Other resources

[Lync Videos on Channel9](http://channel9.msdn.com/tags/lync)

