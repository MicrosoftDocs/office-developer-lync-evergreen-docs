---
title: 'How to: Create and update a Persistent Chat room'
TOCTitle: 'How to: Create and update a Persistent Chat room'
ms:assetid: cc3a1483-3c6e-49e6-a458-756394a599e5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465911(v=office.15)
ms:contentKeyID: 57101434
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Create and update a Persistent Chat room

Learn how to create or update a Persistent Chat room by using the Microsoft Lync Server 2013 Persistent Chat API.


_**Applies to:** Lync 2013 | Lync Server 2013_

In the Lync Server 2013 Persistent Chat API, a chat room is created using [ChatRoomManagementServices](https://msdn.microsoft.com/en-us/library/jj266394\(v=office.15\)).

To create a chat room successfully, the caller must have been granted a role of [Creator](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) in a chat room category that is specified by a Microsoft Lync Server 2013 Persistent Chat administrator. The category of a chat room is also known as the parent category of the chat room. It must be specified when a chat room is created.

To determine whether a user has the permission to create a chat room, the application can search for chat room categories in which the user has been granted the permission. It can do so by calling the [BeginFindCategoriesWithCreateRights(AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267546\(v=office.15\)) and [EndFindCategoriesWithCreateRights(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj266355\(v=office.15\)) methods on [ChatRoomManagementServices](https://msdn.microsoft.com/en-us/library/jj266394\(v=office.15\)).

``` csharp
    ChatRoomManagementServices chatRoomManagementServices = persistentChatEndpoint.PersistentChatServices.ChatRoomManagementServices;
    IAsyncResult asyncResult = chatRoomManagementServices.BeginFindCategoriesWithCreateRights(null, null);
    ReadOnlyCollection<ChatRoomCategorySummary> categories = chatRoomManagementServices.EndFindCategoriesWithCreateRights(asyncResult);
```

When the query returns an empty collection of [ChatRoomCategorySummary](https://msdn.microsoft.com/en-us/library/jj267884\(v=office.15\)), the user cannot create any chat room. Only when non-empty result set is returned, should the caller proceed with room creation under one of the returned categories.

Programmatically, creation of a chat room using the Lync Server 2013 Persistent Chat API involves the following steps:

1.  Obtain an instance of [ChatRoomManagementServices](https://msdn.microsoft.com/en-us/library/jj266394\(v=office.15\)) by calling the [ChatRoomManagementServices](https://msdn.microsoft.com/en-us/library/jj267183\(v=office.15\)) property of the [PersistentChatServices](https://msdn.microsoft.com/en-us/library/jj266890\(v=office.15\)) type.

2.  Specify the chat room settings by using a [ChatRoomSettings](https://msdn.microsoft.com/en-us/library/jj267618\(v=office.15\)) object. The minimum required chat room settings are the name and category of the room. Other information includes the description of the room, an invitation to be sent to newly added members to join the room, a Boolean flag to indicate whether the room is of the auditorium style, or to make the room visible only to its members.

3.  Call the [BeginCreateChatRoom(ChatRoomSettings, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj266391\(v=office.15\)) and [EndCreateChatRoom(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj267626\(v=office.15\)) methods.

The following code example shows how to create a chat room of a given name (chatRoomName) under a given chat room category (parentCategoryUri).

``` csharp
    ChatRoomManagementServices chatRoomMgmt = persistentChatEndpoint.PersistentChatServices.ChatRoomManagementServices;

    ChatRoomSettings settings = new ChatRoomSettings(chatRoomName, parentCategoryUri);
    Uri roomUri = chatRoomMgmt.EndCreateChatRoom((chatRoomMgmt.BeginCreateChatRoom(settings, null, null)));
```

The newly create chat room, as identified by roomUri, is of little use unless a list of members is assigned to it. Otherwise, nobody can participate in chat conversation in the room. The following code example shows how to add the current user to the chat room in the [Creator](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) role.

``` csharp
    // Add current user as member.            
    PersistentChatUserAdministrationServices userMgmt = persistentChatEndpoint.PersistentChatServices.UserAdministrationServices;
    PersistentChatUser user = userMgmt.EndGetUser(userMgmt.BeginGetUser(new Uri(persistentChatEndpoint.InnerEndpoint.OwnerUri), null, null));

    ICollection<PersistentChatPrincipalSummary> members = new List<PersistentChatPrincipalSummary>();
    members.Add(user);
    chatRoomMgmt.EndAddUsersOrGroupsToRole(chatRoomMgmt.BeginAddUsersOrGroupsToRole(ChatRoomRole.Member, roomUri, members, null, null));
```

The same programming pattern can be used to add the user to the chat room in the [Manager](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) role or the [Presenter](https://msdn.microsoft.com/en-us/library/jj266929\(v=office.15\)) role if the chat room is of the auditorium type (that is, [IsAuditorium](https://msdn.microsoft.com/en-us/library/jj266864\(v=office.15\)) = true).


> [!NOTE]
> <P>The user cannot join a chat room session to chat in the underlying chat room unless he or she is a member of the chat room, even if the user is granted a Manager or Presenter role.</P>



When a chat room is created, it can be updated. Commonly used updates include changing the privacy settings of the room. The following code example shows how to update a chat room to the specified privacy settings.

``` csharp
    PersistentChatEndpoint chatEndpoint = ...;
    ChatRoomManagementServices ChatRoomServices = chatEndpoint.PersistentChatServices.ChatRoomManagementServices; 

    public void SetChatRoomPrivacySetting(Uri roomUri, ChatRoomPrivacy privacySetting)
    {
        ChatRoom room = ChatRoomServices.EndGetChatRoom(
            ChatRoomServices.BeginGetChatRoom(roomUri, null, null));
        ChatRoomInformation roomInfo = new ChatRoomInformation(room);
        roomInfo.Privacy = privacySetting;
        ChatRoomServices.EndUpdateChatRoom(
            ChatRoomServices.BeginUpdateChatRoom(roomInfo, null, null));            
    }
```

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

