---
title: Using an AudioVideoFlow
TOCTitle: Using an AudioVideoFlow
ms:assetid: 8d2f16be-724d-4d32-ad34-5ba3e65c80a6
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466032(v=office.15)
ms:contentKeyID: 57103025
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Using an AudioVideoFlow


**Applies to:** Lync 2013 | Lync Server 2013

The [AudioVideoFlow](https://msdn.microsoft.com/library/hh383533\(v=office.15\)), [AudioControl](https://msdn.microsoft.com/library/hh161771\(v=office.15\)), and [AudioChannel](https://msdn.microsoft.com/library/hh349872\(v=office.15\)) classes can be thought of as having the logical relationship shown in the following illustration. The [Audio](https://msdn.microsoft.com/library/hh161753\(v=office.15\)) property on an **AudioVideoFlow** instance provides access to the **AudioControl** instance, and the [GetChannels()](https://msdn.microsoft.com/library/hh383889\(v=office.15\)) method on the **AudioControl** instance returns a read-only **IDictionary** that can be used to find an **AudioChannel** instance by its label.


> [!NOTE]
> <P>In Microsoft Unified Communications Managed API 4.0, an <STRONG>AudioControl</STRONG> instance must have exactly one <A href="https://msdn.microsoft.com/library/hh349872(v=office.15)">AudioChannel</A> instance.</P>



Logical AudioVideoFlow structure

  
![Logical AudioVideoFlow structure](images/Dn466032.AVFlow(Office.15).jpg "Logical AudioVideoFlow structure")

The preceding illustration also shows several of the properties on the three classes. Each property on an outer class affects not only its own class, but can affect an inner class. For example, the [EncryptionPolicy](https://msdn.microsoft.com/library/hh384087\(v=office.15\)) indicates whether channel encryption is not supported, supported, or required, and therefore affects the value of the **Encrypted** property on the **AudioChannel** instance. The [Encrypted](https://msdn.microsoft.com/library/hh384060\(v=office.15\)) value can be true if channel encryption is supported or required, but must be false if channel encryption is not supported.

Because the **AudioVideoFlow** class has no public constructors, it's not possible to directly create an instance of this class. Instead, an application must use the **AudioVideoFlow** instance created when an [AudioVideoCall](https://msdn.microsoft.com/library/hh383901\(v=office.15\)) instance is created (and accessible through the [Flow](https://msdn.microsoft.com/library/hh382705\(v=office.15\)) property on the **AudioVideoCall** instance). If an application intends to change the settings on an **AudioVideoFlow** instance, it must create an [AudioVideoFlowTemplate](https://msdn.microsoft.com/library/hh349157\(v=office.15\)) instance to do so. For more information, see Using an **AudioVideoFlowTemplate**.

