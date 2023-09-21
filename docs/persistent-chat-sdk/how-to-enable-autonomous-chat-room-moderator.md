---
title: 'How to: Enable autonomous chat room moderator'
TOCTitle: 'How to: Enable autonomous chat room moderator'
ms:assetid: 0c30fc5e-7b71-4b8b-8304-b16d530511c3
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465903(v=office.15)
ms:contentKeyID: 57101390
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Enable autonomous chat room moderator

Learn how to create an autonomous chat room moderator in a Microsoft Lync Server 2013 Persistent Chat deployment.


**Applies to:** Lync 2013 | Lync Server 2013

When a chat room is dedicated to discussions about a specific subject, it's often desirable that the administrator can enforce the discussions to comply with the related topics or specified policies. For example, a family-oriented forum will want to ensure that inappropriate words or expressions not be posted or redacted. Similarly, a customer support chat room dedicated to a specific product can keep the discussions focused on the specified product by removing comments or messages about other products from the chat rooms.

In the Lync Server 2013 Persistent Chat an administrator can enforce such policies by manually inspecting the messages posted to a chat room and calling the [Remove-CsPersistentChatMessage](https://msdn.microsoft.com/library/jj204668\(v=office.15\)) cmdlet to remove any messages containing inappropriate words or phrases according to a prescribed policy. However, this manual process is not most efficient. An automated approach is more desirable. The Microsoft Lync Server 2013 Persistent Chat API, together with Microsoft Unified Communications Managed API 4.0 and the [System.Automation.Management](http://msdn.microsoft.com/library/windows/desktop/system.management.automation\(v=vs.85\).aspx) namespace, can be used to enable such a scenario.

The automated approach involves creating a Microsoft Unified Communications Managed API 4.0 bot application that also uses the Lync Server 2013 Persistent Chat API to connect to the Lync Server 2013 Persistent Chat on an [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\))-based [PersistentChatEndpoint](https://msdn.microsoft.com/library/jj267567\(v=office.15\)) and to receive messages posted to the chat room the bot signs in to. As a Lync Server trusted application, the bot can act with the privileges of the Lync Server 2013 Persistent Chat administrator to invoke the PowerShell cmdlet programmatically whenever a message contains offensive terms. In effect, the application serves as an autonomous moderator for the given chat room.

## Create an autonomous chat room moderator

Creating an autonomous chat room moderator typically involves the following programming tasks:

1.  Connect to Microsoft Lync Server 2013 on an [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)) that is also trusted by the server.

2.  Connect to the Lync Server 2013 Persistent Chat on the [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\))-based [PersistentChatEndpoint](https://msdn.microsoft.com/library/jj267567\(v=office.15\)).

3.  Select a chat room to moderate.

4.  Establish a session with the chat room and register to receive [ChatMessageReceived](https://msdn.microsoft.com/library/jj266375\(v=office.15\)) events raised in the session.

5.  Call the **Remove-CsPersistentChatMessage** cmdlet to remove or replace any terms in a list of blocked words or phrases.

6.  In the event handler for the [ChatMessageReceived](https://msdn.microsoft.com/library/jj266375\(v=office.15\)) events, invoke the PowerShell cmdlet to remove or replace any terms in a list of blocked words or phrases.

## See also

#### Concepts

[Scenarios for using Persistent Chat API](scenarios-for-using-persistent-chat-api.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

