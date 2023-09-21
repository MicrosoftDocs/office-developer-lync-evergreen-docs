---
title: Chat room content maintenance
TOCTitle: Chat room content maintenance
ms:assetid: 5d8eb16b-c7a7-4130-b42f-5bab60140d31
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465891(v=office.15)
ms:contentKeyID: 57101352
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Chat room content maintenance

Learn how access to Persistent Chat room data is controlled by user roles.


**Applies to:** Lync 2013 | Lync Server 2013

Persistent Chat lets users collaborate by posting messages in Persistent Chat rooms. The data is stored on the server and members of the chat room can have access to the data, including historical data. However, access to the stored data is controlled by the user role, as outlined in the following list:

  - Administrators can delete older content (for example, content posted before a certain date) from any chat room to keep the size of the database from growing greatly. They can also remove or replace messages considered unsuitable for a given chat room.

  - End users, including message authors, cannot delete content from any chat room.

  - Chat room managers can disable rooms, but cannot delete rooms. Only administrators can delete a chat room after it is created.

When a message is deleted, you cannot undo the action. However, deleted messages can be restored if there is a backup. If a Persistent Chat Compliance Server is enabled, old messages are stored in the compliance database.


> [!NOTE]
> <P>This chat room data usage applies to the Lync Server 2013 Persistent Chat API application, except for the case when the administrator role is involved. The Lync Server 2013 Persistent Chat API cannot be used to perform any of the administrator’s operations. These must be performed in the Lync Server Management Shell.</P>



## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK documentation](lync-server-2013-persistent-chat-sdk-documentation.md)

[How to: Manage Persistent Chat users and user groups](how-to-manage-persistent-chat-users-and-user-groups.md)

#### Other resources

[Lync Server Management Shell](http://technet.microsoft.com/library/gg398474.aspx)

