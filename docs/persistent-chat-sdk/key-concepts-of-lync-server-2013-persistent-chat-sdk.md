---
title: Key concepts of Lync Server 2013 Persistent Chat SDK
TOCTitle: Key concepts
ms:assetid: dd457a91-5abd-4f98-bb5e-a86da06f5045
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465894(v=office.15)
ms:contentKeyID: 57101348
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Key concepts of Lync Server 2013 Persistent Chat SDK

Learn about Microsoft Lync Server 2013 Persistent Chat API programming concepts.


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
Persistent Chat rooms  
Chat room categories  
Roles  
Scope  
User and user groups  

The Lync Server 2013 Persistent Chat API exposes functionality for building a wide variety of applications, including automated chat Bots, administrative tools, simple mobile or Web clients, and gateways or interfaces to bridge the Persistent Chat room application with other systems.

To use the Lync Server 2013 Persistent Chat API, you should have a basic understanding of the concepts discussed in the following sections.

## Persistent Chat rooms

A Persistent Chat room is a topic-oriented forum for multi-party collaboration. Simple text messages, files, and a variety of formatted text elements including hyperlinks, chat room links, and emoticons can be posted to a chat room to share with other participants. Messages are delivered to active participants of the chat room in real time. When a user joins a chat room at a later time, he or she can retrieve a configurable number of previously posted messages that provide contextual history of the conversation. The chat history of all rooms is also searchable in a variety of ways. Hence, a Persistent Chat room provides a long-lived repository of information that teams can use to collaborate with each other over time.

## Chat room categories

A chat room category is a grouping mechanism for organizing and managing persistent chat rooms. Microsoft Lync Server 2013 Persistent Chat defines a top-level category, sometimes called the root category, and administrators can define one level of subcategories under the root category.

Every chat room must be rooted in exactly one chat room category under the root category. No chat rooms are rooted in the root category. The category to which a chat room belongs is called its parent category. By default, a chat room inherits many of its settings from its parent category.

A category is typically used to configure access to the rooms of the category. For more information, see the **Roles** description below.

## Roles

Security of Persistent Chat rooms is controlled by lists of users and user groups who are granted various roles. Roles can be defined by listing individual users, or more commonly, by specifying an Active Directory container, security group, or distribution list. By using an Active Directory group to manage chat rooms, roles are maintained automatically as the group is updated in Active Directory.

Roles can be specified in categories. A category determines and puts boundaries for who can put rooms in that category and who can be members of rooms that belong in that category. This is enforced using the following roles:

  - **AllowedMember**  
    The AllowedMembers on a category determines the set of users from which you can choose the membership of a room that you choose to put in that category.

  - **Creator**  
    The Creators on a category determines who can create rooms in that category. When a room is created, typically an end user cannot move it to another category. When a room is created, to move the room to another category, the user needs to be a creator in the new category as well.

The following roles are defined for chat rooms:

  - **Member**  
    A user that has permission to join a Persistent Chat room and participate in the conversation. To be added as a member, a user must be in the defined scope list of the parent category.

  - **Manager**  
    A user that has permission to modify the role lists and change the settings of a persistent chat room. A user in the **Manager** role cannot join the chat room unless the user is also in the **Member** role.

  - **Presenter**  
    When a chat room is of the auditorium type (that is, when the [IsAuditorium](https://msdn.microsoft.com/en-us/library/jj266864\(v=office.15\)) property is set to **true** in the room) a user can be a presenter or regular member in the chat room. The default value of this setting is false. However, if the value is set to true, the chat room only permits users who are granted the role of presenter to post messages in the chat room. All members can join and read messages, but permission to post new messages is restricted in this scenario.

Similarly, a chat room category also defines a set of roles. The roles on a category serve a dual purpose. First, they define the default role list of child nodes in the category. Second, they grant specific permissions for actions on the category.

## Scope

Unlike what was referenced in Microsoft Lync Server 2010, scope now refers to allowed or denied users specified for a given chat room. The scope of a category is defined as the list of users and user groups from which members, presenters, managers or creators of the category may be selected. In other words, a user cannot be a member, presenter, manager, or creator of a chat room, unless he or she is in scope on the parent category. The scope rules extend to all rooms of the category, thus giving the category manager the ability to ensure that no chat room in his or her area contains members outside of the organizations he or she wants to collaborate with.


> [!NOTE]
> <P>Category scope and creator list are only editable by the administrator through the Lync server Management Shell cmdlets and the feature is not exposed in the API.</P>



## User and user groups

Microsoft Lync Server 2013 Persistent Chat supports Active Directory users and user groups for the purpose of defining roles and scope on Persistent Chat rooms and chat room categories. Users and user groups are collectively referred to as principals when they are used for Persistent Chat administration. In addition to being used for defining roles and scope, a principal can be granted one or more roles in a chat room. The supported roles are enumerated in the [ChatRoomRole](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) type.

  - **AD User**  
    Any user defined in Active Directory who is SIP enabled for Microsoft Lync Server 2013 can participate in a Persistent Chat.

  - **AD Container**  
    An Active Directory container, such as a domain or organizational unit, can be used to define roles. When installed, the domain to which the administrator who performs the installation is assigned is used for the initial root category scope. User administrators can add additional principals to the root category scope as needed.

  - **AD Security Group or Distribution List**  
    An Active Directory security group can be defined as a member of a Persistent Chat room. Because a security group can cross organizational boundaries, and because scope can only be narrowed, a security group cannot be used to manage the scope of a category unless it is explicitly defined on the parent category scope. This means that any security group to be used in this fashion must be defined on the root category scope and inherited by every subcategory scope list to the point in the category hierarchy where its usage is desired.

## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK documentation](lync-server-2013-persistent-chat-sdk-documentation.md)

