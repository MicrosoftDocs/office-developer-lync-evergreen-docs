﻿---
title: Contacts and groups
TOCTitle: Contacts and groups
ms:assetid: 7a28afda-a9e1-43aa-b5ec-cc403ecb8df2
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465965(v=office.15)
ms:contentKeyID: 57102663
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Contacts and groups


**Applies to:** Lync 2013 | Lync Server 2013

A contact is a presentity whose presence information is tracked. A contact registers its status, location, and other attributes with the Microsoft Lync Server 2013 computer. Contacts can be organized into user-defined groups. In Microsoft Unified Communications Managed API 4.0, contacts and groups are supported only by [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\)) objects. The [ContactGroupServices](https://msdn.microsoft.com/library/hh383122\(v=office.15\)) property on a **UserEndpoint** instance provides access to a [ContactGroupServices](https://msdn.microsoft.com/library/hh381099\(v=office.15\)) instance, which an application can use to add or remove groups, or update groups by adding or removing contacts. Contacts can be associated with one or more groups. The **ContactGroupServices** class provides methods to subscribe or unsubscribe to a user’s contacts or groups, as well as to refresh the subscription. To update an instance of a contact or a group, an application supplies an existing contact or group instance to the **ContactGroupServices** API, modifies the specific fields of interest, and then publishes the new item.

A contact can be identified by its URI, and a group can be identified by its group ID, which is assigned by Lync Server 2013 when the group is created. An application can use methods on the **ContactGroupServices** class to obtain a contact or group, by using the contact URI or group ID. When an application deletes a group, all of the contacts who belong to the group are updated by the removal of their references to that group.

For more information, see [ContactGroupServices](contactgroupservices.md).

