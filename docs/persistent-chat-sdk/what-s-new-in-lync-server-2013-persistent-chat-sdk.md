---
title: What's new in Lync Server 2013 Persistent Chat SDK
TOCTitle: What's new
ms:assetid: aad090a4-8a48-4a48-82db-2807822f9881
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439200(v=office.15)
ms:contentKeyID: 57101265
ms.date: 07/24/2014
mtps_version: v=office.15
---

# What's new in Lync Server 2013 Persistent Chat SDK

Learn about new Microsoft Lync Server 2013 Persistent Chat SDK features.


**Applies to:** Lync 2013 | Lync Server 2013

Group Chat is now rebranded as Persistent Chat. Hence, Microsoft Group Chat Server API is now known as Microsoft Persistent Chat Server API.

In addition to rebranding, Microsoft Lync 2013 includes the following changes to Persistent Chat client functionality:

  - The Persistent Chat client functionality is now supported through Lync 2013. A separate standalone Persistent Chat client is no longer supported.

  - The backend server has gone through many changes, resulting in the following impact to Lync Server 2013 Persistent Chat API:
    
      - The API exposes a simplified administration model with a single level of categories and simplified inheritance of properties between categories and rooms. As a result, there are changes to the API to accommodate for this change in the core model.
    
      - The administration and management functionalities to create and manage categories and add-ins are now exposed only to the administrator through Windows PowerShell. As a result, this functionality is not exposed by the Lync Server 2013 Persistent Chat API. The API allows an application to read predefined categories and add-ins and to create and manage chat rooms. The API permits the end user to create and manage chat rooms as well.
    
      - User administration in Persistent Chat is now role-based in a manner that is consistent with Microsoft Lync 2013. As a result, the Lync Server 2013 Persistent Chat API supports read-only access of user's permissions.

For details of the updates, see the following topics:

  - [Updated object model](updated-object-model.md)

  - [Class library changes](class-library-changes.md)

  - [Changes in technical requirements](changes-in-technical-requirements.md)

## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK documentation](lync-server-2013-persistent-chat-sdk-documentation.md)

#### Other resources

[Lync Videos on Channel9](http://channel9.msdn.com/tags/lync)

