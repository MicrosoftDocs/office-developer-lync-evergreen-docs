---
title: Terminology of Lync Server 2013 Persistent Chat SDK
TOCTitle: Terminology
ms:assetid: 88433af4-9be0-4f2d-8c0b-d86df7a4e014
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439209(v=office.15)
ms:contentKeyID: 57101358
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Terminology of Lync Server 2013 Persistent Chat SDK

Learn about Microsoft Lync Server 2013 Persistent Chat SDK terminology.


**Applies to:** Lync 2013 | Lync Server 2013


## A

  - **Active Chat Room Session**  
    A session that is currently joined. All active Persistent Chat room sessions can be accessed by using the name and URI indexers on the [PersistentChatEndpoint](https://msdn.microsoft.com/library/jj267567\(v=office.15\)) class. When a user leaves the chat room, the session is removed from the Active Chat Room Session collection.

  - **Add-in**  
    A small webpage or web application that is displayed in a panel beneath the chat input area in Microsoft Lync Server 2013 Persistent Chat. Lync Server 2013 Persistent Chat publishes a set of events and metadata about the chat room to the add-in, and permits the add-in limited access to interact with both inbound and outbound messages in a real time fashion.

  - **Alert**  
    A Persistent Chat message that is posted with higher than normal priority. Microsoft Lync Server 2013 Persistent Chat displays these messages in red, and produces an audible queue when they arrive.

  - **Auditorium**  
    A property that can be enabled on a Persistent Chat room that restricts the posting of messages to members that have a presenter role.

## C

  - **Category**  
    A hierarchical construct for organizing and managing Persistent Chat rooms. Categories are largely used for management of chat rooms and do not play a significant role in the user experience for Microsoft Lync Server 2013 Persistent Chat.

  - **Chat Room**  
    A persistent, topic-oriented, access-controlled forum for collaboration where multiple users share text messages and files in real time, and have access to historical chat room messages by search or by contextual history. A chat room can have three levels of privacy settings: open, closed, or secret. An open chat room is visible to and can be joined by all users in scope on the parent category. A closed chat room is visible to all users in scope on the parent category but can be joined only by members of the chat room, whereas a secret chat room is visible only to members of the chat room.

  -  **Chat Room Link**  
    A hyperlink that points to a chat room. It can be entered into current chat room messages to point users to another chat room.

  - **Chat Room Session**  
    A class in the Microsoft Lync Server 2013 Persistent Chat API that can be used to join a Persistent Chat room and participate in a conversation.

  - **Creator**  
    A role assigned to a user who has permission to create a Persistent Chat room. The role is specified as part of category specification.

## E

  - **Emoticon**  
    An approximation of a facial expression that is usually entered by using punctuation characters, and often translated by text messaging applications into a small image of the corresponding facial expression.

## H

  - **History**  
    The set of contextual chat messages that users generally retrieve when they first join a Persistent Chat room. History can be retrieved by context (number of recent messages desired) or by query (using parameters such as author, message content, or date).

## I

  - **Invitation**  
    A notification that a Persistent Chat user receives when added to a Persistent Chat room. Past invitations can be requested, and they are sent in batches. Invitations are only issued when the chat room specifically enables the feature by using the [SendInvitationsToMembers](https://msdn.microsoft.com/library/jj267873\(v=office.15\)) property. Due to the performance implications of large channel invites, this feature should be used sparingly.

## J

  - **Join**  
    The act of establishing a Persistent Chat room session and initiating the receipt of real-time messages. A user must have a member role on a chat room to join a closed or secret chat room session, but can join an open chat room without the membership requirement.

## K

  - **Kick**  
    The message that an active chat room user receives when the member role is revoked. A kick message removes a user from a Persistent Chat room, and stops the delivery of future messages.

## L

  - **Large Chat Room**  
    A Persistent Chat room that has more than the server configured maximum number of active participants. The default value for the maximum number of participants is 75. Once the number of active participants exceeds 75, the server stops sending notifications of Join and Part events when users enter or leave the chat room. The server also stops automatically sending the current active user list to new users when they enter the chat room. The server reverts to standard chat room behavior when the Large Chat Room falls below 80 percent of the maximum number of active participants.

## M

  - **Managers**  
    Principals (users and user groups) who have been granted a role which permits them to edit properties of a Persistent Chat room or chat room category.

  - **Members**  
    Principals who have been granted a role which permits them to join a closed or secret Persistent Chat room and participate in the conversation.

## P

  - **Participant**  
    A user that is actively joined to a Persistent Chat room, and receives messages in real time.

  - **Part (Leave)**  
    The message that an active chat room user sends to the server when he or she wishes to stop participating in a Persistent Chat room and receive real time updates. Also known as Leave.

  - **Permissions**  
    Rights that can be granted to a principal that permit them to perform actions such as file posting and Persistent Chat room administration.

  - **Persistent Chat**  
    Formally known as Group Chat, Persistent Chat supports multiparty conversations that persist over time. Conversations occur in Persistent chat rooms, which are topic oriented, access controlled forums for posting real-time messages to be shared with a group of users.

  - **Preferences**  
    Application specific user data that can be stored on Microsoft Lync Server 2013 Persistent Chat. Lync Server 2013 Persistent Chat uses preferences in an unpublished format to store Persistent Chat rooms and display settings that the user has selected. Microsoft Lync Server 2013 Persistent Chat API developers can use this feature to store custom data or settings that is needed for their application.

  - **Presenters**  
    Principals who have been granted a role that permits them to post chat messages in a Persistent Chat room that restricts chat message posting by using the [IsAuditorium](https://msdn.microsoft.com/library/jj266864\(v=office.15\)) property.

  - **Principal**  
    A generic term which refers to any user or user group.

## R

  - **Role**  
    A set of privileges granted to a collection of users and user groups for a specific Persistent Chat room or category of chat rooms. Examples of a role include member, manager, and presenter.

## S

  - **Scope**  
    Refers to allowed members as specified on a Persistent Chat room category. The scope (the allowed members) of a category is defined as the list of users and user groups from which members of the category may be selected. A user cannot be a member of a chat room unless he or she is in scope on the parent category. The scope rules extend to all child nodes of the category, thus giving the category manager the ability to insure that no chat room in his or her area contains members outside of the organizations he or she wishes to collaborate with.

  - **Snapshot**  
    An object which briefly describes a Persistent Chat room and the active user count of the chat room. It's returned from many of the Browse operations in the Microsoft Lync Server 2013 Persistent Chat API.

  - **Story**  
    A lengthy Persistent Chat room message that includes of a story title, and a long message. The long message is hidden in the chat display, but remains searchable, and viewable when a user clicks the corresponding link that is shown.
    
    A lengthy chat room message that includes of a title and a body. When Microsoft Lync Server 2013 Persistent Chat receives a story message, it displays only the title of the message in the chat room display window as a highlighted link. When the user clicks the title, the entire message appears in a separate dialog. The content of a story message is stored in the same way as a normal chat room message, and is fully searchable when querying chat history.

## U

  - **User Group**  
    An active directory container, security group, or distribution list that is permissioned for a specific role in Persistent Chat.

## V

  - **Visibility**  
    A property that applies to a Persistent Chat room to indicate the visibility of the room to search. When the [VisibleOnlyToMembers](https://msdn.microsoft.com/library/jj266336\(v=office.15\)) property is set to true, only members of the chat room will find it in searches. When false, any user in scope on the category can see the chat room in a search.

## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK documentation](lync-server-2013-persistent-chat-sdk-documentation.md)

