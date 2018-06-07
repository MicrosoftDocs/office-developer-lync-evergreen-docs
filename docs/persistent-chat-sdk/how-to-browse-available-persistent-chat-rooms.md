---
title: 'How to: Browse available Persistent Chat rooms'
TOCTitle: 'How to: Browse available Persistent Chat rooms'
ms:assetid: 3b664f00-56bb-46b3-b39d-54cdf3617ba9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465907(v=office.15)
ms:contentKeyID: 57101413
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Browse available Persistent Chat rooms

Learn how to browse the available Persistent Chat rooms in a Microsoft Lync Server 2013 Persistent Chat deployment.


**Applies to:** Lync 2013 | Lync Server 2013

When a [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)) instance is connected to a Lync Server 2013 Persistent Chat, its state becomes [Established](https://msdn.microsoft.com/en-us/library/jj267239\(v=office.15\)) and the endpoint-based Persistent Chat services that are encapsulated by [PersistentChatServices](https://msdn.microsoft.com/en-us/library/jj266890\(v=office.15\)) becomes operational immediately. Such services include browsing available chat rooms by calling [BeginBrowseChatRoomsByCriteria(String, Boolean, Boolean, Boolean, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267603\(v=office.15\)), [BeginBrowseChatRoomsByInvitations(Int32, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267594\(v=office.15\)), [BeginBrowseChatRoomsByJoinedUser(Uri, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj266317\(v=office.15\)), [BeginBrowseChatRoomsIManage(AsyncCallback, Object, UInt32)](https://msdn.microsoft.com/en-us/library/jj266916\(v=office.15\)), or [BeginBrowseMyChatRooms(AsyncCallback, Object, UInt32)](https://msdn.microsoft.com/en-us/library/jj267602\(v=office.15\)) method on the [PersistentChatServices](https://msdn.microsoft.com/en-us/library/jj266890\(v=office.15\)) type. These methods are asynchronous and the operations must be completed by calling the corresponding EndBrowseXXX method. The following example shows how to invoke these methods to browse available persistent chat rooms on a Persistent Chat server.

``` csharp
        public void BrowseChatRooms(PersistentChatEndpoint chatEndpoint, string criteria, ref int lastInviteId, string userSipUri)
        {
            PersistentChatServices chatServices = chatEndpoint.PersistentChatServices;
            var rooms = chatServices.EndBrowseChatRoomsByCriteria(
                chatServices.BeginBrowseChatRoomsByCriteria(criteria, true, false, false, null, null)
                );
            ShowBrowseChatRoomsResults("Criteria", rooms);

            rooms = chatServices.EndBrowseChatRoomsByInvitations(
                chatServices.BeginBrowseChatRoomsByInvitations(lastInviteId, null, null), out lastInviteId
                );
            ShowBrowseChatRoomsResults("Invitations", rooms);

            rooms = chatServices.EndBrowseChatRoomsByJoinedUser(
                chatServices.BeginBrowseChatRoomsByJoinedUser(new Uri(userSipUri), null, null)
                );
            ShowBrowseChatRoomsResults("JoinedUser", rooms);

            rooms = chatServices.EndBrowseMyChatRooms(
                chatServices.BeginBrowseMyChatRooms(null, null, 10)
                );
            ShowBrowseChatRoomsResults("MyChatRooms", rooms);

            rooms = chatServices.EndBrowseChatRoomsIManage(
                chatServices.BeginBrowseChatRoomsIManage(null, null, 10)
                );
            ShowBrowseChatRoomsResults("IManage", rooms);

       }

        void ShowBrowseChatRoomsResults(string browseMode, ReadOnlyCollection<ChatRoomSnapshot> res)
        {
            Console.WriteLine("Browse Chat Rooms by {0}", browseMode);
            foreach (var r in res)
            {
                Console.WriteLine("Name={0}\tDescription={1}\tNumber of participants={2}\tChatRoomUri={3}",
                    r.Name, r.Description, r.NumberOfParticipants, r.ChatRoomUri.ToString());
            }
        }
```

The results returned from browsing chat rooms methods are a collection of [ChatRoomSnapshot](https://msdn.microsoft.com/en-us/library/jj267241\(v=office.15\)) objects. The [ChatRoomUri](https://msdn.microsoft.com/en-us/library/jj266377\(v=office.15\)) property on this kind of object can be used to join a chat room. For more information, see [How to: Join and leave a Persistent Chat room session](how-to-join-and-leave-a-persistent-chat-room-session.md).

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

