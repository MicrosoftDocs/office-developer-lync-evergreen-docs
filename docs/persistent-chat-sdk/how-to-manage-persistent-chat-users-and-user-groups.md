---
title: 'How to: Manage Persistent Chat users and user groups'
TOCTitle: 'How to: Manage Persistent Chat users and user groups'
ms:assetid: 163a5e5b-010e-481d-a818-a2d3378d3f9d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465904(v=office.15)
ms:contentKeyID: 57101398
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Manage Persistent Chat users and user groups

Learn how to manage Persistent Chat users and user groups by using the Microsoft Lync Server 2013 Persistent Chat API.


**Applies to:** Lync 2013 | Lync Server 2013

The Lync Server 2013 Persistent Chat API provides the following user administration services, which are encapsulated by the [PersistentChatUserServices](https://msdn.microsoft.com/en-us/library/jj265986\(v=office.15\)) type:

  - Find Persistent Chat users with matching first name, last name, or email address.

  - Retrieve a Persistent Chat user of a given SIP URI.

  - Get detailed information of a Persistent Chat user group.

The user services are exposed by the [UserServices](https://msdn.microsoft.com/en-us/library/jj266379\(v=office.15\)) property on the [PersistentChatServices](https://msdn.microsoft.com/en-us/library/jj266890\(v=office.15\)) type.

To find Persistent Chat users with matching first name, last name, or email address, call [BeginFindUsers(String, String, String, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj265879\(v=office.15\)) followed by [EndFindUsers(IAsyncResult, Boolean)](https://msdn.microsoft.com/en-us/library/jj267276\(v=office.15\)). The following code example shows how to find all users whose first name is John, whose last name is Doe, or whose email address is johndoe@contoso.com.

``` csharp
         PersistentChatEndpoint chatEndpoint = …;
         PersistentChatUserServices ChatUserServices = chatEndpoint.PersistentChatServices.UserServices;
    bool moreAvailable;
    var res = ChatUserServices.EndFindUsers(
        ChatUserServices.BeginFindUsers("Doe", "John", "johndoe@contoso.com", null, null),
        out moreAvailable);
    if (moreAvailable)
        Console.WriteLine("Only a subset of the results are returned. You may need to retry with more restricted search criteria");
```

When the output parameter moreAvailable returns true, some results are truncated and not returned. An application might want to retry the search by restricting the search criteria.

The results are returned as a collection of [PersistentChatPrincipalSummary](https://msdn.microsoft.com/en-us/library/jj267859\(v=office.15\)) objects. Each of such objects is a lightweight version of the [PersistentChatPrincipal](https://msdn.microsoft.com/en-us/library/jj266388\(v=office.15\)) object and contains a subset of the information about a user or group, including the name, SIP URI, and type of an Active Directory security principal object matching specified search criteria. For a user, the principal type is [LocalUser](https://msdn.microsoft.com/en-us/library/jj267557\(v=office.15\)). For a user group, the principal type is [DirectoryGroup](https://msdn.microsoft.com/en-us/library/jj267557\(v=office.15\)), [DirectoryFolder](https://msdn.microsoft.com/en-us/library/jj267557\(v=office.15\)) or [Domain](https://msdn.microsoft.com/en-us/library/jj267557\(v=office.15\)).

To retrieve a Persistent Chat user of a given SIP URI, call [BeginGetUser(Uri, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267227\(v=office.15\)) followed by [EndGetUser(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj266902\(v=office.15\)). The following code example shows how to get the complete user information from the first entry of a user query against a given first name, last name, or email address.

``` csharp
PersistentChatEndpoint chatEndpoint = ...;
PersistentChatUserServices ChatUserServices = chatEndpoint.PersistentChatServices.UserServices;

public PersistentChatUser GetUser(string lastName, string firstName, string email)
{
    bool moreAvailable;
    PersistentChatPrincipalSummary ps = ChatUserServices.EndFindUsers(
        ChatUserServices.BeginFindUsers(lastName, firstName, email, null, null), out moreAvailable).FirstOrDefault();
    if (ps == null)
        return null;
    PersistentChatUser pu = ChatUserServices.EndGetUser(
        ChatUserServices.BeginGetUser(ps.Uri, null, null));
    return pu;
}
```


> [!NOTE]
> <P>The <STRONG>GetUser</STRONG> operation succeeds only when the caller is a System User or when the caller tries to get the detailed user information about himself or herself. Otherwise, a <STRONG>CommandFailedException</STRONG> is raised stating that the caller is not authorized to perform the action.</P>



In the example above, if the search returns an empty results set, the **GetUser** routine returns null. Otherwise, the first entry of the search results is used as the intended user. The final result is a [PersistentChatUser](https://msdn.microsoft.com/en-us/library/jj267549\(v=office.15\)) object. It inherits from [PersistentChatPrincipal](https://msdn.microsoft.com/en-us/library/jj266388\(v=office.15\)) and exposes additional information pertinent to the user, including the company name, display name, and email address, as well as whether the user is disabled for Persistent Chat or not.

To get detailed information of Persistent Chat user group, call [BeginGetUserGroup(PersistentChatPrincipalSummary, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267230\(v=office.15\)) followed by [EndGetUserGroup(IAsyncResult)](https://msdn.microsoft.com/en-us/library/jj267610\(v=office.15\)). The following code example shows how to get a Persistent Chat user group of a given name (groupName) intended for the specified chat room (roomUri).

``` csharp
PersistentChatEndpoint chatEndpoint = ...;

public PersistentChatUserGroup GetUserGroup(Uri roomUri, string groupName)
{
    ChatRoomManagementServices rms = chatEndpoint.PersistentChatServices.ChatRoomManagementServices;
    PersistentChatPrincipalSummary pSummary = rms.EndFindUsersOrGroupsForRole(
        rms.BeginFindUsersOrGroupsForRole(ChatRoomRole.Member, roomUri, groupName, null, null)).FirstOrDefault();
    if (pSummary == null)
        return null;
    PersistentChatUserServices pus = chatEndpoint.PersistentChatServices.UserServices;
    PersistentChatUserGroup pug = pus.EndGetUserGroup(pus.BeginGetUserGroup(pSummary, null, null));
    return pug;
}
```


> [!NOTE]
> <P>The <STRONG>GetUserGroup</STRONG> operation succeeds only when the caller is a System User. Otherwise, a <STRONG>CommandFailedException</STRONG> is raised stating that the caller is not authorized to perform the action.</P>



The returned results are a collection of [PersistentChatUserGroup](https://msdn.microsoft.com/en-us/library/jj266882\(v=office.15\)) objects.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

