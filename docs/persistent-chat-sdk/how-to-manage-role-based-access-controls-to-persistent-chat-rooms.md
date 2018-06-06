---
title: 'How to: Manage role-based access controls to Persistent Chat rooms'
TOCTitle: 'How to: Manage role-based access controls to Persistent Chat rooms'
ms:assetid: 73f67797-b48b-4cb5-97b7-d4baeb7ce46f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465902(v=office.15)
ms:contentKeyID: 57101388
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Manage role-based access controls to Persistent Chat rooms

Learn how to manage role-based access controls to Persistent Chat rooms by using the Microsoft Lync Server 2013 Persistent Chat API.


_**Applies to:** Lync 2013 | Lync Server 2013_

Managing user roles in a chat room amounts to maintaining access control to the chat room by specified users. The Lync Server 2013 Persistent Chat API exposes three levels of access control. These are enumerated as [Member](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)), [Manager](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)), and [Presenter](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)). The [Creator](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) role is specified in a category and not accessible programmatically.

Making a user a member of a chat room involves adding the user to the chat room in the [Member](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) role. Similarly, making a user a manager or presenter involves adding the user in the [Manager](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) or [Presenter](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) role. These can be accomplished by calling the [BeginAddUsersOrGroupsToRole(ChatRoomRole, Uri, ICollection\<PersistentChatPrincipalSummary\>, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267275\(v=office.15\)) followed by [EndAddUsersOrGroupsToRole(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj266344\(v=office.15\)).


> [!NOTE]
> <P>To be in a <A href="https://msdn.microsoft.com/en-us/library/jj266929(v=office.15)">Presenter</A> role, the chat room must be of the auditorium type.</P>



To deny the access to a chat room by a user, simply remove the user from the chat room in his or her given role. This is done by calling the [BeginRemoveUsersOrGroupsFromRole(ChatRoomRole, Uri, ICollection\<PersistentChatPrincipalSummary\>, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj266883\(v=office.15\)) followed by [EndRemoveUsersOrGroupsFromRole(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj266858\(v=office.15\)).

The following code example shows how to add a user to a chat room in a given role. The chat room is the first one managed by the currently signed-in user. The to-be-added user is identified by his email address ("johndoe@contoso.com") and retrieved by calling the [BeginFindUsersOrGroupsForRole(ChatRoomRole, Uri, String, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj266406\(v=office.15\)) and [EndFindUsersOrGroupsForRole(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj267864\(v=office.15\)).

``` csharp
    PersistentChatServices chatServices = persistentChatEndpoint.PersistentChatServices;
    var roomSum = chatServices.EndBrowseChatRoomsIManage(
        chatServices.BeginBrowseChatRoomsIManage(null, null, 100)).FirstOrDefault();
    if (roomSum != null)
   {
       Uri = roomSum.ChatRoomUri;
       var pSums = ChatRoomServices.EndFindUsersOrGroupsForRole(
          ChatRoomServices.BeginFindUsersOrGroupsForRole(
            role,
            roomUri,
            "johndoe@contoso.com",
            null, null));
       if (pSums.Count > 0)
       {
          ChatRoomServices.EndAddUsersOrGroupsToRole(
            ChatRoomServices.BeginAddUsersOrGroupsToRole(
                role,
                roomUri,
                pSums,
                null, null));
        }
    } 
```

To verify whether the user has been added to a chat room in a given role, the application can call [BeginGetMembers(Uri, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj266927\(v=office.15\)), [BeginGetManagers(Uri, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267314\(v=office.15\)), and [BeginGetPresenters(Uri, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267236\(v=office.15\)) followed by [EndGetMembers(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj267865\(v=office.15\)), [EndGetManagers(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj267228\(v=office.15\)), or [EndGetPresenters(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj267554\(v=office.15\)), respectively.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

