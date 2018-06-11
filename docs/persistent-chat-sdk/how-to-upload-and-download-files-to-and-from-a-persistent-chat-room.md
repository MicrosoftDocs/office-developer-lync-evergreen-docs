---
title: 'How to: Upload and download files to and from a Persistent Chat room'
TOCTitle: 'How to: Upload and download files to and from a Persistent Chat room'
ms:assetid: b9ba6339-00bd-4a33-bad0-3f18178260cd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465909(v=office.15)
ms:contentKeyID: 57101435
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Upload and download files to and from a Persistent Chat room

Learn how to transfer files to and from a Persistent Chat room by using the Microsoft Lync Server 2013 Persistent Chat API.


**Applies to:** Lync 2013 | Lync Server 2013

To upload files to a Persistent Chat room, the chat room must be configured to support file upload. This feature is controlled at the category level by the system administrator. When a chat room supports file upload, the established chat room session has its [IsFilePostAllowed](https://msdn.microsoft.com/en-us/library/jj267250\(v=office.15\)) property set to true. If this is false, uploading files to the underlying chat room will not succeed.

## Uploading a file to a Persistent Chat room

To upload a file to a joined chat room, call the [BeginUploadFile(ChatRoomFileUploadJob, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj266370\(v=office.15\)) and [EndUploadFile(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj266919\(v=office.15\)) methods on a [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) instance that has established a connection to the given chat room. The to-be-uploaded file is passed in to the call by using a [ChatRoomFileUploadJob](https://msdn.microsoft.com/en-us/library/jj265934\(v=office.15\)) object, which also allows an application to monitor the progress of a file upload by raising the [ProgressChanged](https://msdn.microsoft.com/en-us/library/jj266417\(v=office.15\)) events. To monitor the progress of a file upload job, an application must register for the event and implement an event handler.

The following code example shows how to upload a file to a chat room by using the Lync Server 2013 Persistent Chat API. The file is identified by the fileToUpload input parameter. The chat room is specified by the roomUri value. In the following example, the event handling of the [ProgressChanged](https://msdn.microsoft.com/en-us/library/jj266417\(v=office.15\)) event is implemented by the job\_ProgressChanged routine.

```csharp
PersistentChatEndpoint chatEndpoint = ...;
ChatRoomSession ChatSession = new ChatRoomSession(chatEndpoint);

public void UploadFile(Uri roomUri, System.IO.FileInfo fileToUpload)
{
    if (!ChatSession.IsFilePostAllowed)
        return;
    JoinChatRoom(roomUri);

    ChatRoomFileUploadJob job = new ChatRoomFileUploadJob(fileToUpload);
    job.ProgressChanged += new EventHandler<ChatRoomFileTransferProgressEventArgs>(job_ProgressChanged);
    ChatSession.EndUploadFile(
        ChatSession.BeginUploadFile(job, null, null));
    LeaveChatRoom(roomUri);
}

void job_ProgressChanged(object sender, ChatRoomFileTransferProgressEventArgs e)
{
    Console.WriteLine("TotalBytes={0}, Percent transferred={1}%", e.TotalBytes, e.PercentTransferred);
}
```

One way to get a file is to use the **OpenFileDialog** control in the System.Windows.Forms namespace, as shown in the following code example.

```csharp
static System.IO.FileInfo GetFileToOpen()
{
    System.Windows.Forms.OpenFileDialog ofd = new System.Windows.Forms.OpenFileDialog();
    if (System.Windows.Forms.DialogResult.OK == ofd.ShowDialog())
        return new System.IO.FileInfo(ofd.FileName);
    else
        return null;
}
```

## Downloading a file from a Persistent Chat room

To download a file from a joined chat room, call the [BeginDownloadFile(ChatRoomFileDownloadJob, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj266877\(v=office.15\)) and [EndDownloadFile(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj267254\(v=office.15\)) methods on a [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) instance that has established a connection to the given chat room. The to-be-downloaded file is passed in to the call by using a [ChatRoomFileDownloadJob](https://msdn.microsoft.com/en-us/library/jj266867\(v=office.15\)) object, which also allows an application to monitor the progress of a file upload by raising [ProgressChanged](https://msdn.microsoft.com/en-us/library/jj265868\(v=office.15\)) events. To monitor the progress of a file download job, an application must register for the event and implement an event handler.

The following code example shows how to download a file from a chat room by using the Lync Server 2013 Persistent Chat API. The to-be-downloaded file is the first one retrieved from the given chat room. It is extracted from a [ChatMessage](https://msdn.microsoft.com/en-us/library/jj266914\(v=office.15\)) instance containing the file. The implementation is shown in the GetFileDownloadLink routine where the [MessagePartFileDownloadLink](https://msdn.microsoft.com/en-us/library/jj265937\(v=office.15\)) object (downloadLink) is obtained by casting the [MessagePart](https://msdn.microsoft.com/en-us/library/jj265942\(v=office.15\)) of a [ChatMessage](https://msdn.microsoft.com/en-us/library/jj266914\(v=office.15\)) in the chat room. The destinationPath variable specifies the location where the downloaded file is saved. The chat room is specified by the roomUri value. The event handling of the [ProgressChanged](https://msdn.microsoft.com/en-us/library/jj265868\(v=office.15\)) event uses the same job\_ProgressChanged routine that is used to upload the file job.

```csharp
public void DownloadFile(Uri roomUri, string destinationPath)
{
    if (!ChatSession.IsFilePostAllowed)
        return;

    JoinChatRoom(roomUri);
    var downloadLink = GetFileDownloadLink(roomUri);
    ChatRoomFileDownloadJob job = new ChatRoomFileDownloadJob(downloadLink, destinationPath);
    job.ProgressChanged += new EventHandler<ChatRoomFileTransferProgressEventArgs>(job_ProgressChanged);
    ChatSession.EndDownloadFile(
        ChatSession.BeginDownloadFile(job, null, null));
    LeaveChatRoom(roomUri);
}

MessagePartFileDownloadLink GetFileDownloadLink(Uri roomUri)
{
    ChatHistoryQueryOptions query = new ChatHistoryQueryOptions(null);            
    var chatHistory = ChatSession.EndQueryChatHistory(
        ChatSession.BeginQueryChatHistory(query, null, null));
    foreach (ChatMessage message in chatHistory.Messages)
    {
        foreach (MessagePart part in message.FormattedMessageParts)
        {
            if (part is MessagePartFileDownloadLink)
            {
                return part as MessagePartFileDownloadLink;
            }
        }
    }
    return null;
}
```


> [!NOTE]
> <P>Files posted to a chat room will not be available to users of Microsoft Lync 2013.</P>



## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

