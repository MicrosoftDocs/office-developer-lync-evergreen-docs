---
title: 'How to: Show automaton presence to PIC clients'
TOCTitle: 'How to: Show automaton presence to PIC clients'
ms:assetid: 191ab030-24e6-4cec-86ea-f4edc57f5b6d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439075(v=office.15)
ms:contentKeyID: 57096234
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Show automaton presence to PIC clients

Learn how to configure automaton bot presence for Public Internet Cloud (PIC) clients in a Microsoft Lync Server 2013 server deployment.


_**Applies to:** Lync 2013 | Lync Server 2013_

In a Lync Server 2013 server deployment, an automaton corresponds to an Active Directory **Contact** object. It is used to represent an application or service with a routable SIP address. Known as a bot, this kind of application serves as a middle-tier between the server and a client and provides automated communication services. An example is a bot that functions as a help desk to connect a customer to a support staff based on the customer’s answers to questions posed by the bot. The bot can be a Microsoft Unified Communications Managed API (UCMA) application that is routed through a UCMA [ApplicationEndpoint](https://msdn.microsoft.com/en-us/library/hh384825\(v=office.15\)) instance and is trusted by Lync Server 2013. A bot can be used as an autonomous communication service. To use the service, a client must connect to an enabled bot and start a conversation with the bot through IM or by using other enabled modalities. This implies that the client must subscribe to or query the bot’s presence status. When the bot is online, the client can start a conversation with it.

In practical applications, lots of users might want to use the bot’s services. This means that the bot will have a large list of subscribers. However, to conserve resources on the server, Lync Server 2013 limits the subscribers for each presentity. As a consequence, the presence of a popular bot is made available to several subscribers that cannot exceed the number of default server endpoints. At any time some clients might access the bot, although others might not. In a period of time, a client might connect to the bot at some times, but not at other times. To avoid this experience, Microsoft Lync 2013 implements a custom logic when it subscribes to the presence of automatons. Essentially, when Lync 2013 signs in to the Lync Server 2013 instance, it starts a subscription to receive the presence of the entities in the user’s contact list. If a bot is in the contact list, Lync removes it from the subscription as soon as it receives its presence status. It then caches the obtained presence status and displays it to show the availability of the bot until the client endpoint is disposed of. This is reasonable because an enabled bot is always online. This way, the user is not counted as a registered subscriber of the bot, the bot does not exceed its subscription limit, and the user has consistent communication with the bot.

However, other clients (for example, PIC clients like Windows Live Messenger, Skype, and Yahoo\! Messenger) are not required to implement the same logic. To prevent this kind of client from overwhelming the subscription limit on a bot, Lync Server 2013 always returns Offline or Presence Unknown when this kind of client attempts to subscribe to the bot’s presence. This means that the services that are offered by the bot cannot be extended to users beyond the enterprise network that hosts the Lync Server 2013 without circumventing this restriction.

To extend a bot’s service across or beyond enterprise network boundaries, the correct presence status of the bot must be returned to a PIC client. One way to do this is to enable a Lync Server 2013 SIP Application API application that maintains the knowledge of the installed bots on the server, intercepts incoming subscription requests from a PIC client, and returns the Online presence status for the bot if the target of the request matches an installed bot. For a subscription request from a non-PIC client, the application has to route the request back to the server, which handles the request as usual. For information about how to build this application, see [Extending Unified Communications services of UCMA Bots to PIC Clients](http://msdn.microsoft.com/en-us/library/jj128288).

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

[Scenarios for using the Lync Server 2013 API](scenarios-for-using-the-lync-server-2013-api.md)

#### Other resources

[Extending Unified Communications Services of UCMA Bots to PIC Clients](http://msdn.microsoft.com/en-us/library/jj128288)

