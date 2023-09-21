---
title: 'How to: Join and leave a Persistent Chat room session'
TOCTitle: 'How to: Join and leave a Persistent Chat room session'
ms:assetid: ad6df682-54e6-46c9-92a6-1a1b932d1fc6
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465898(v=office.15)
ms:contentKeyID: 57101359
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Join and leave a Persistent Chat room session

Learn how to use the Microsoft Lync Server 2013 Persistent Chat API to join or leave a Persistent Chat room session.


**Applies to:** Lync 2013 | Lync Server 2013

Certain Persistent Chat functionalities are session-based. These include operations to be performed against or within a specific chat room. For example, posting messages to a chat room or receiving messages in real-time from the chat room takes place in a session. In Lync Server 2013 Persistent Chat API, a session is encapsulated by the [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) type. When connected, the chat room session is said to be [Established](https://msdn.microsoft.com/library/jj267274\(v=office.15\)).

To join a Persistent Chat room session, an instance of [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) must be created and then the [BeginJoin(ChatRoomSummary, AsyncCallback, Object)](https://msdn.microsoft.com/library/jj265923\(v=office.15\))/[EndJoin(IAsyncResult)](https://msdn.microsoft.com/library/jj266330\(v=office.15\)) methods or one of their overloads are invoked on an established [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) object that has not been terminated. In addition, the room-join operation will fail unless the user is a member of the chat room. A user is a member of a chat room if she or he is explicitly added to the chat room in the Member role. The user is not a member even if she or he was previously added to the room in the Manager role. A presenter must also be a member.

There are several ways to specify the chat room to join. You can use a chat room name, the chat room’s URI, or chat room information as encapsulated by the [ChatRoomSummary](https://msdn.microsoft.com/library/jj267628\(v=office.15\)) type. In the following code example, a chat room URI is used to join the specified chat room.

An established chat room session corresponds to a joined chat room. A user can send a chat message only to joined chat room by using the corresponding established chat room session. To check whether the chat room session is established, examine the [State](https://msdn.microsoft.com/library/jj265902\(v=office.15\)) property.

To send a message to a different chat room, a new chat room session instance or an existing chat room session instance can be used. If an existing chat room session instance is used, the chat room session must first leave the already joined chat room before it can join the new chat room. To leave a joined chat room, call the [BeginLeave(AsyncCallback, Object)](https://msdn.microsoft.com/library/jj266411\(v=office.15\)) and [EndLeave(IAsyncResult)](https://msdn.microsoft.com/library/jj267521\(v=office.15\)) methods on an established [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) instance.

Before sending any messages to a chat room, verify that the connection to the chat room is established. This is accomplished by monitoring the [ChatRoomSessionStateChanged](https://msdn.microsoft.com/library/jj267324\(v=office.15\)) event that is raised from the chat room session. In the following code example, this is done by registering for the [ChatRoomSessionStateChanged](https://msdn.microsoft.com/library/jj267324\(v=office.15\)) event and implementing the event handler as cr\_Session\_ChatRoomSessionStateChanged.

When a participant sends a message to the chat room, the corresponding [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) object raises a [ChatMessageReceived](https://msdn.microsoft.com/library/jj266375\(v=office.15\)) event. To get notified of this event, an application can register for handling this event.

The following example shows how to join a chat room by using a new [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) instance. The newly instantiated chat room session is ready when the [ChatRoomSessionStateChanged](https://msdn.microsoft.com/library/jj267324\(v=office.15\)) event returns with an Established state.

```csharp
        public void JoinChatRoom(Uri chatRoomUri)
        {
            ChatRoomSession crSession = new ChatRoomSession(_chatServices.Endpoint);
                                 
            // Register for events raised in this chat room session.
            crSession.ChatMessageReceived += new EventHandler<ChatMessageReceivedEventArgs>(crSession_ChatMessageReceived);
            crSession.ChatRoomSessionStateChanged += new EventHandler<ChatRoomSessionStateChangedEventArgs>(crSession_ChatRoomSessionStateChanged);

            crSession.EndJoin(crSession.BeginJoin(chatRoomUri, null, null));           
        }

        void crSession_ChatRoomSessionStateChanged(object sender, ChatRoomSessionStateChangedEventArgs e)
        {
            Console.WriteLine("Chat room session state = {0}", e.State);
            ChatRoomSession session = sender as ChatRoomSession;

            if (e.State == ChatRoomSessionState.Established)
                session.EndSendChatMessage(session.BeginSendChatMessage("Hi.", null, null));
            else if (e.State == ChatRoomSessionState.Terminating)
                session.EndSendChatMessage(session.BeginSendChatMessage("Bye.", null, null));
         }

        void crSession_ChatMessageReceived(object sender, ChatMessageReceivedEventArgs e)
        {
            ChatRoomSession session = sender as ChatRoomSession;

            if (session != null && session.Endpoint.InnerEndpoint.OwnerUri != e.Message.MessageAuthor.OriginalString)
            {
                Console.WriteLine("Message received from room {0} ({1})", e.Message.ChatRoomName, e.Message.ChatRoomUri);
                Console.WriteLine("\tby author: {0}", e.Message.MessageAuthor.OriginalString);
                Console.WriteLine("\tConent: {0}", e.Message.MessageContent);
                  FormattedOutboundChatMessage focMsg = new FormattedOutboundChatMessage();
                  focMsg.AppendEmoticon(ChatEmoticon.Wink);
                  focMsg.AppendPlainText("Like");
                  session.EndSendChatMessage(session.BeginSendChatMessage(focMsg, null, null));

            }
        }
```

The following code example shows how to join or leave a chat room by using an existing [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) instance.

```csharp
        void JoinChatRoom(Uri roomUri, ChatRoomSession chatRoomSession)
        {
            if (chatRoomSession == null)
                return;
            if (chatRoomSession.State == ChatRoomSessionState.Established)
                chatRoomSession.EndLeave(chatRoomSession.BeginLeave(null, null));
            chatRoomSession.EndJoin(chatRoomSession.BeginJoin(roomUri, null, null));
        }

        void LeaveChatRoom(Uri roomUri, ChatRoomSession chatRoomSession)
        {
            if (chatRoomSession != null && chatRoomSession.State == ChatRoomSessionState.Established)
                chatRoomSession.EndLeave(chatRoomSession.BeginLeave(null, null));
        }
```

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

