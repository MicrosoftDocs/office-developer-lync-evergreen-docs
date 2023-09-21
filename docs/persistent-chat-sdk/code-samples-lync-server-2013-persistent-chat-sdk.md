---
title: Code samples (Lync Server 2013 Persistent Chat SDK)
TOCTitle: Code samples
ms:assetid: 8e963d23-6e9f-4e73-aaa2-8a3044db788a
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465915(v=office.15)
ms:contentKeyID: 57101440
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Code samples (Lync Server 2013 Persistent Chat SDK)

Learn about the Microsoft Lync Server 2013 Persistent Chat SDK sample applications and learn how to build and run each application.


**Applies to:** Lync 2013 | Lync Server 2013

The following Lync Server 2013 Persistent Chat SDK sample applications show how the Microsoft Lync Server 2013 Persistent Chat API can be used to connect to and disconnect from the Microsoft Lync Server 2013 Persistent Chat instance, send and receive chat messages, and search and manage chat rooms and users.


> [!NOTE]
> <P>By default, all applications are installed in the %ProgramFile%\Microsoft Lync Server 2013\Persistent Chat SDK\ folder. The following samples and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/">MSDN Code Gallery</A>.</P>



  - SampleChat

  - SampleLoadTest

  - SampleRiamo

  - SampleSearchRooms

The SampleCommon.cs file is not a full sample on its own and contains a set of utility functions that are used by the four samples discussed in this section. To compile and run a sample, integrate SampleCommon.cs into a Microsoft Visual Studio project along with the code for the given sample.

## In this section

  - [Create and join a chat room and participate in chat (SampleChat)](create-and-join-a-chat-room-and-participate-in-chat-samplechat.md)
    
    Demonstrates how to create and join a chat room and then post chat messages in the chat room.

  - [Maintain load-balance on the server (SampleLoadTest)](maintain-load-balance-on-the-server-sampleloadtest.md)
    
    Simulates a multiple-user load on the server and assumes the users are created and SIP-enabled. The sample creates the category and chat rooms necessary to run the sample if they are not present.

  - [Retrieve chat rooms by using user membership (SampleRiamo)](retrieve-chat-rooms-by-using-user-membership-sampleriamo.md)
    
    Demonstrates how to retrieve a list of chat rooms of which the user is a member or manager.

  - [Search for chat rooms (SampleSearchRooms)](search-for-chat-rooms-samplesearchrooms.md)
    
    Demonstrates how to search for chat rooms using the Lync Server 2013 Persistent Chat API.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

#### Other resources

[Lync Videos on Channel9](http://channel9.msdn.com/tags/lync)

