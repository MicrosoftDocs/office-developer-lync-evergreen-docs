---
title: 'How to: Send and receive Persistent Chat messages'
TOCTitle: 'How to: Send and receive Persistent Chat messages'
ms:assetid: 1f6c92b4-191c-47e6-ada9-235f96eafadf
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465900(v=office.15)
ms:contentKeyID: 57101372
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Send and receive Persistent Chat messages

Learn how to use the Microsoft Lync Server 2013 Persistent Chat API to send or receive Persistent Chat room messages.


**Applies to:** Lync 2013 | Lync Server 2013

Sending and receiving messages are session-based operations and require that the underlying chat room session be established. In the Lync Server 2013 Persistent Chat API, chat messages can be of plain text and RTF and can include hyperlinks and emoticons.

To send message to a Persistent Chat room by using the Lync Server 2013 Persistent Chat API, call one of the [BeginSendChatMessage(String, AsyncCallback, Object)](https://msdn.microsoft.com/library/jj266943\(v=office.15\)) methods and the corresponding [EndSendChatMessage(IAsyncResult)](https://msdn.microsoft.com/library/jj267874\(v=office.15\)) method on an established [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) instance.

The following code example shows how to send a plain text message (txtMsg) to a chat room that is connected to an established [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) instance (chatRoomSession).

```csharp
        void SendTextMessage(ChatRoomSession chatRoomSession, string txtMsg)
        {
            if (chatRoomSession != null && chatRoomSession.CanChat)
            {
                chatRoomSession.EndSendChatMessage(
                    chatRoomSession.BeginSendChatMessage(txtMsg, null, null));
            }
        }
```

The following code example shows how to use the Lync Server 2013 Persistent Chat API to send an RTF message to a chat room that is connected to a specified, established [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) instance (chatRoomSession). The rich text message was extracted from a RichTextBox control (richTextBox).


> [!NOTE]
> <P>An RTF message is sent along with a plain text message. When done this way, any legacy Persistent Chat client can still receive the chat message even if it is not RTF-enabled.</P>



```csharp
        void SendRtfMessage(ChatRoomSession chatRoomSession, RichTextBox richTextBox)
        {
            if (chatRoomSession != null && chatRoomSession.CanChat)
            {
                string txtContent = richTextBox1.Text;
                string rtfContent = richTextBox1.Rtf;
                chatRoomSession.EndSendChatMessage(
                    chatRoomSession.BeginSendChatMessage(txtContent, rtfContent, null, null));
            }
        }
```

The following code example shows how to use the Lync Server 2013 Persistent Chat API to send a formatted message (focm) to add a hyperlink (hyperLlink), or an emoticon (emoticon), as part of a plain text message (plaintext) to a chat room that is connected to a specified, established [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) instance (chatRoomSession).

```csharp
        void SendFormattedMessage(ChatRoomSession chatRoomSession, string plainText, ChatEmoticon emoticon, string hyperLinkText, Uri hyperLink)
        {
            if (chatRoomSession != null && chatRoomSession.CanChat)
            {
                FormattedOutboundChatMessage focm = new FormattedOutboundChatMessage();
                focm.AppendEmoticon(emoticon);
                focm.AppendHyperLink(hyperLinkText, hyperLink);
                focm.AppendPlainText(plainText);
                chatRoomSession.EndSendChatMessage(
                    chatRoomSession.BeginSendChatMessage(focm, null, null));
            }           
        }
```

Other overloads are available to support the process of sending a chat message to a chat room by using the Lync Server 2013 Persistent Chat API.

To receive messages when a new message is posted to a chat room, register the [ChatMessageReceived](https://msdn.microsoft.com/library/jj266375\(v=office.15\)) event to be raised by an established [ChatRoomSession](https://msdn.microsoft.com/library/jj265925\(v=office.15\)) instance and handle the event in an event handler.

The following code example shows how to register for the [ChatMessageReceived](https://msdn.microsoft.com/library/jj266375\(v=office.15\)) event and provides an example of the event handler, which simply prints the received message.

```csharp
        void RegisterToReceiveChatMessage(ChatRoomSession chatRoomSession)
        {
            if (chatRoomSession != null)
            {
                chatRoomSession.ChatMessageReceived += new EventHandler<ChatMessageReceivedEventArgs>(chatRoomSession_ChatMessageReceived);
            }
        }

        void chatRoomSession_ChatMessageReceived(object sender, ChatMessageReceivedEventArgs e)
        {
            ShowReceivedChatMessage(e.Message);
        }

        void ShowReceivedChatMessage(ChatMessage msg)
        {
            Console.WriteLine("Received chat received:");
            Console.WriteLine("{0} ({1})", msg.ChatRoomName, msg.ChatRoomUri.ToString());
            Console.WriteLine("On {0} {1} wrote: ", msg.Timestamp.ToLocalTime().ToString(), msg.MessageAuthor.OriginalString);
            Console.WriteLine("content: {0}", msg.MessageContent);
            Console.WriteLine("Rtf content {0}", msg.MessageRtfContent);
            foreach (MessagePart msgPart in msg.FormattedMessageParts)
                Console.WriteLine("DisplayText: {0}\r\nRawText: ", msgPart.DisplayText, msgPart.RawText);
        }
```

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

