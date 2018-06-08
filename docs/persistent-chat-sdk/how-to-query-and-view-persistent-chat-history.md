---
title: 'How to: Query and view Persistent Chat history'
TOCTitle: 'How to: Query and view Persistent Chat history'
ms:assetid: 1978038f-3a01-4ba1-a822-7fb87b9ac081
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465910(v=office.15)
ms:contentKeyID: 57101419
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Query and view Persistent Chat history

Learn how to use the Microsoft Lync Server 2013 Persistent Chat API to query the chat history for a Persistent Chat room.


**Applies to:** Lync 2013 | Lync Server 2013

There are two ways to use the Lync Server 2013 Persistent Chat API to query chat history for a chat room.

The first way involves calling the [BeginQueryChatHistory(ChatHistoryQueryOptions, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267612\(v=office.15\)) and [EndQueryChatHistory(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj267871\(v=office.15\)) methods on an established [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) instance. The chat history of the underlying chat room is returned in a [ChatHistoryResult](https://msdn.microsoft.com/en-us/library/jj267589\(v=office.15\)) object.

In addition, query options can be specified to conduct a query for chat messages that contain specified phrases (searchString), sent by specified users (authors) between given starting and ending dates (beginDate and endDate). The query options can also be specified by using the [ChatHistoryQueryOptions](https://msdn.microsoft.com/en-us/library/jj265933\(v=office.15\)) type. This concept is shown in the following code example, where a query is made to search for chat messages in a specified chat room (roomUri) sent between January 2, 2011 and November 23, 2011. The results, as encapsulated in a [ChatHistoryResult](https://msdn.microsoft.com/en-us/library/jj267589\(v=office.15\)) object, are shown under a specified TreeView node (parent).

```csharp
        void ShowQueryChatHistoryInRoom(Uri roomUri, TreeNode parent)
        {
           if (roomUri == null || parent == null)
               return;

           if (_chatRoomSession.State != ChatRoomSessionState.Established)
               JoinChatRoom(roomUri);
           if (_chatRoomSession.State == ChatRoomSessionState.Established && _chatRoomSession.ChatRoomUri != roomUri)
           {
               LeaveChatRoom();
               JoinChatRoom(roomUri);
           }

            if (_chatRoomSession.State != ChatRoomSessionState.Established)
                return;

            ChatHistoryQueryOptions queryOptions = new ChatHistoryQueryOptions("");
            queryOptions.DateBeginning = new DateTime(2011, 1, 2);
            queryOptions.DateEnding = new DateTime(2011, 11, 23);

            var history = _chatRoomSession.EndQueryChatHistory(
                _chatRoomSession.BeginQueryChatHistory(queryOptions, null, null));

            parent.Nodes.Clear();
            TreeNode root = new TreeNode("Chat history: (SearchResultsCount=" + history.SearchResultsCount + "; ExceededServerLimit=" + history.ExceededServerLimit + ")");
            parent.Nodes.Add(root);

            TreeNode child, node;
            foreach (var msg in history.Messages)
            {
                string display = msg.Timestamp.ToLocalTime().ToString() + ", " + msg.MessageAuthor.OriginalString + ":";
                node = new TreeNode(display);
                root.Nodes.Add(node);

                child = new TreeNode("Content: " + msg.MessageContent);
                node.Nodes.Add(child);
                foreach (var part in msg.FormattedMessageParts)
                {
                    child.Nodes.Add(new TreeNode("FormattedMsgPart.DisplayText = " + part.DisplayText));
                    child.Nodes.Add(new TreeNode("FormattedMsgParts.RawText = " + part.RawText));
                }

                child = new TreeNode("RtfContent: " + msg.MessageRtfContent);
                node.Nodes.Add(child);
                foreach (var part in msg.FormattedRtfMessageParts)
                {
                    child.Nodes.Add(new TreeNode("FormattedRtfMsgPart.DisplayText = " + part.DisplayText));
                    child.Nodes.Add(new TreeNode("FormattedRtfMsgParts.RawText = " + part.RawText));
                }
            }
        }
```

The second way involves calling the [BeginQueryChatHistory(ICollection\<Uri\>, ChatHistoryQueryOptions, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267261\(v=office.15\)) method and the corresponding [EndQueryChatHistory(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj266316\(v=office.15\)) method on the [PersistentChatServices](https://msdn.microsoft.com/en-us/library/jj266890\(v=office.15\)) type. This call requires a specification of Persistent Chat rooms of which the history is to be retrieved. The result is returned as a read-only collection of [ChatHistoryResult](https://msdn.microsoft.com/en-us/library/jj267589\(v=office.15\)) objects. The caller must be a member of the chat rooms for the query to return meaningful results, although the caller does not need to join the rooms. Query options can be specified as well.

```csharp
        public ReadOnlyCollection<ChatHistoryResult> QueryChatHistory(
            ICollection<Uri> chatRoomUris, string searchString, bool exactPhrase, bool caseSensitive)
        {
            return _chatServices.EndQueryChatHistory(
                _chatServices.BeginQueryChatHistory(chatRoomUris, searchString, exactPhrase, caseSensitive, null, null)
                );
        }
```

The Lync Server 2013 Persistent Chat API also supports the retrieval of recent chat history from a joined chat room. This involves calling the [BeginGetRecentChatHistory(Int32, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj266863\(v=office.15\)) and [EndGetRecentChatHistory(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj266402\(v=office.15\)) methods on an established [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) instance. The results are returned as a read-only collection of [ChatMessage](https://msdn.microsoft.com/en-us/library/jj266914\(v=office.15\)) objects. This concept is shown in the following code example, where a number (number) of recent chat messages are retrieved from a given chat room (roomUri). The returned results, as a collection of the ReadOnlyCollection\<ChatMessage\> type, are displayed under a given TreeNode node (parent).

```csharp
        void ShowGetRecentChatHistoryInRoom(Uri roomUri, TreeNode parent, int number)
        {
            if (roomUri == null || parent == null)
                return;

            if (_chatRoomSession.State == ChatRoomSessionState.Established)
                LeaveChatRoom(_chatRoomSession);
            
            JoinChatRoom(roomUri, _chatRoomSession);

            var history = _chatRoomSession.EndGetRecentChatHistory(
                _chatRoomSession.BeginGetRecentChatHistory(number, null, null));

            parent.Nodes.Clear();
            TreeNode root = new TreeNode("Recent chat history:");
            parent.Nodes.Add(root);

            TreeNode child, node;
            foreach (var chatMsg in history)
            {                
                var msgParts = chatMsg.FormattedMessageParts;
                var rtfMsgParts = chatMsg.FormattedRtfMessageParts;
                node = new TreeNode(chatMsg.Timestamp.ToLocalTime().ToString() + ". Is alert msg: " + chatMsg.IsAlert);
                root.Nodes.Add(node);
                node.Nodes.Add(new TreeNode("Content: " + chatMsg.MessageContent));
                node.Nodes.Add(new TreeNode("RtfContent: " + chatMsg.MessageRtfContent));
                node.Nodes.Add(new TreeNode("Author: " + chatMsg.MessageAuthor.OriginalString));

                child = new TreeNode("FormattedMessageParts:");
                node.Nodes.Add(child);
                foreach (var msgPart in chatMsg.FormattedMessageParts)
                {
                    child.Nodes.Add(new TreeNode("DisplayText: " + msgPart.DisplayText));
                    child.Nodes.Add(new TreeNode("RawText: " + msgPart.RawText));
                }

                child = new TreeNode("FormattedMessageParts:");
                node.Nodes.Add(child);
                foreach (var msgPart in chatMsg.FormattedRtfMessageParts)
                {
                    child.Nodes.Add(new TreeNode("DisplayText: " + msgPart.DisplayText));
                    child.Nodes.Add(new TreeNode("RawText: " + msgPart.RawText));
                }
            }
        }
```

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

