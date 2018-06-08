---
title: Features and architecture of Lync Server 2013 Persistent Chat SDK
TOCTitle: Features and architecture
ms:assetid: 04f5f7ad-e0e0-4eb5-b671-bee20b5f21d6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439211(v=office.15)
ms:contentKeyID: 57101355
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Features and architecture of Lync Server 2013 Persistent Chat SDK

Learn about the Persistent Chat features that are distributed with the Microsoft Lync Server 2013 Persistent Chat API.


**Applies to:** Lync 2013 | Lync Server 2013

 

The Lync Server 2013 Persistent Chat API provides the programming interface for Persistent Chat in a Lync Server deployment. The API enables an application to support the following three major Persistent Chat feature sets:

  - Enable a user to participate in a chat room. The participation includes posting messages to the chat room, receiving viewable messages. The messaging takes place in real time and persisted messages can be queried at a later time. A chat room consists of a group of participants and contains a collection of persisted messages posted by the participants. A chat room is encapsulated by the **ChatRoom** class.
    
    To post a message to chat room or to receive a message from the chat room in real time, the user must first join the chat room. In this case, the user is said to be in an active chat room session. A chat room session is encapsulated by the **ChatRoomSession** class in the [Microsoft.Rtc.Collaboration.PersistentChat](https://msdn.microsoft.com/en-us/library/jj267586\(v=office.15\)) namespace. A user can post a message only in an active chat room session, although the user can receive messages from an inactive chat room using queries. In addition to posting and receiving messages, the user can upload or download files in an active chat room session. An active chat room session becomes terminated when the user leaves the chat room.

  - Enable a user of the application to perform certain chat room management services. The services include creating or updating a chat room, finding or retrieving a chat room based on certain criterion, granting or denying permissions for users to access a chat room, and retrieving participants in given roles from a chat room. The room management services are encapsulated by the **ChatRoomManagementServices** class in the [Microsoft.Rtc.Collaboration.PersistentChat.Management](https://msdn.microsoft.com/en-us/library/jj267343\(v=office.15\)) namespace.

  - Enable a user of the application to find and obtain Persistent Chat users or groups in the underlying Active Directory. The user management services are encapsulated by the [PersistentChatUserServices](https://msdn.microsoft.com/en-us/library/jj265986\(v=office.15\)) class in the [Microsoft.Rtc.Collaboration.PersistentChat.Management](https://msdn.microsoft.com/en-us/library/jj267343\(v=office.15\)) namespace.

The entry point for all the functionality in the Lync Server 2013 Persistent Chat API is the [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)) class. All other functionality is tied directly or indirectly to an instance of this class, which is connected to the underlying Persistent Chat server in a Lync server deployment. Programmatically, a [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)) instance connected to a Persistent Chat server is derived from a [LocalEndpoint](https://msdn.microsoft.com/en-us/library/hh349887\(v=office.15\)) instance connected to the underlying Lync Server. For a client-like application, the [LocalEndpoint](https://msdn.microsoft.com/en-us/library/hh349887\(v=office.15\)) instance is of the [UserEndpoint](https://msdn.microsoft.com/en-us/library/hh348819\(v=office.15\)) type. For a server-like application, the [LocalEndpoint](https://msdn.microsoft.com/en-us/library/hh349887\(v=office.15\)) instance is of the [ApplicationEndpoint](https://msdn.microsoft.com/en-us/library/hh384825\(v=office.15\)) type. For information about working with local endpoints, see [Microsoft.Rtc.Collaboration Namespace](http://go.microsoft.com/fwlink/?linkid=157301).


> [!NOTE]
> <P>Support of <A href="https://msdn.microsoft.com/en-us/library/hh384825(v=office.15)">ApplicationEndpoint</A>-based <A href="https://msdn.microsoft.com/en-us/library/jj267567(v=office.15)">PersistentChatEndpoint</A> is enabled in Microsoft Lync Server 2013 Persistent Chat. However, such a <A href="https://msdn.microsoft.com/en-us/library/jj267567(v=office.15)">PersistentChatEndpoint</A> instance must correspond to an object in the Active Directory domain namespaces and cannot be one in the Active Directory Configuration namespaces. Typically, this implies that an Active Directory User object be used to enable the server-side Lync Server 2013 Persistent Chat API application. Any request initiated from a <A href="https://msdn.microsoft.com/en-us/library/jj267567(v=office.15)">PersistentChatEndpoint</A> derived from an Active Directory Contact object will be refused by Microsoft Lync Server 2013 Persistent Chat. This means that the <A href="https://msdn.microsoft.com/en-us/library/hh384825(v=office.15)">ApplicationEndpoint</A> used in the server-side application can have a SIP URI of a regular user, but not that a trusted application endpoint configured by the <A href="http://technet.microsoft.com/en-us/library/gg398594.aspx">New-CsTrustedApplicationEndpoint</A> cmdlet.</P>



The Lync Server 2013 Persistent Chat API is composed of a set of classes that include asynchronous methods, properties, and events. To provide adequate performance and to be consistent with the UCMA 4.0 SDK, the Lync Server 2013 Persistent Chat API supports the BeginXxx/EndXxx pattern to implement asynchronous operations. For more information, see [Asynchronous Programming Overview](http://go.microsoft.com/fwlink/?linkid=157303).

The following illustration displays the main classes that you will work with in the Lync Server 2013 Persistent Chat API.

![objectModel](images/Dn439211.objectModel(Office.15).jpg "objectModel")

## Persistent Chat endpoint

In addition to maintaining a connection to the Persistent Chat server, an established [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)) object also serves as an event sink to get notified when the user receives an invitation to join a chat room. An Persistent Chat API application can elect to receive such events by subscribing to the **ChatRoomInvitationReceived()** event.

The Persistent Chat endpoint also maintains a collection of the active chat room sessions the user enabled on the endpoint. This collection of active chat room sessions is exposed by the **ActiveChatRoomSessions()** property.

Various Persistent Chat services are made available to an application via the [PersistentChatServices](https://msdn.microsoft.com/en-us/library/jj265982\(v=office.15\)) property, which returns a **PersistentChatServices** object. The Persistent Chat services are explained next.

## Persistent Chat services

The [PersistentChatServices](https://msdn.microsoft.com/en-us/library/jj266890\(v=office.15\)) class provides access to a wide variety of Persistent Chat room features and services. Some administrative functionality and all client services, with the exception of establishing a [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) instance, are exposed through this object. In addition to the methods provided for browsing the catalog of available chat rooms, this class exposes the following properties:

  - [ChatRoomManagementServices](https://msdn.microsoft.com/en-us/library/jj267183\(v=office.15\))  
    Supports methods for managing chat rooms, including finding chat room categories assigning the [Creator](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) role to the caller; browsing available chat rooms; creating or updating a chat room, provided that the caller has the permission as specified in a chat room category; determining the eligibility of users for a given role in a chat room and granting or denying the role for the users; and examining the membership of a chat room.

  - [UserServices](https://msdn.microsoft.com/en-us/library/jj266379\(v=office.15\))  
    Supports methods to query and retrieve Persistent Chat users or user groups from the underlying Active Directory.

## Persistent Chat room session

The [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) class provides functionality that can be used to participate in the conversation of a chat room. This object must be constructed with an established instance of [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)). When constructed, you can choose to subscribe to one or more events to be notified of incoming chat and changes to the metadata of the chat room. After all events are properly configured, you must invoke the **BeginJoin(...)** method to establish connectivity and enter the chat room.

When the session is joined, a reference to the [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) is stored in the collection of [ActiveChatRoomSessions](https://msdn.microsoft.com/en-us/library/jj265900\(v=office.15\)) on the [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)) and you can use any of the methods provided for interacting with the chat room. The session remains active until you invoke the **BeginLeave(...)** method, which initiates a request to leave the chat room and stop the delivery of new messages and notifications.

## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK documentation](lync-server-2013-persistent-chat-sdk-documentation.md)

