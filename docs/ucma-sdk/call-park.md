﻿---
title: Call park
TOCTitle: Call park
ms:assetid: 555e8378-4124-49d8-bada-08dc636bde33
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466006(v=office.15)
ms:contentKeyID: 57102971
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Call park


**Applies to:** Lync 2013 | Lync Server 2013

An application might find it necessary to place a caller on hold temporarily, and then have a different user or application retrieve the call later. The caller on hold is said to be "parked." The call parking concept is typically applied to audio calls, but can be extended to other media types when appropriate. When a user successfully parks a call, the far-end caller is connected to a music-on-hold server and is disconnected from the person who parks the call. The parked call, which is identified by string of decimal digits (an "orbit" number) that uniquely identifies the call, can be retrieved at a later time by any user who is able to provide the orbit number. After the parked call is retrieved, the connection to the music-on-hold server is broken, and the user whose call was parked is reconnected to the retriever. If a parked call is not retrieved within a specific amount of time, the call parking service informs the person who parked the call.

The first two methods in the following list can be used to park a call. The last two methods in the list can be used to retrieve a parked call.

  - [BeginPark](https://msdn.microsoft.com/library/hh384250\(v=office.15\))

  - [EndPark](https://msdn.microsoft.com/library/hh349305\(v=office.15\))

  - [BeginEstablish](https://msdn.microsoft.com/library/hh349055\(v=office.15\))

  - [EndEstablish](https://msdn.microsoft.com/library/hh349248\(v=office.15\))

