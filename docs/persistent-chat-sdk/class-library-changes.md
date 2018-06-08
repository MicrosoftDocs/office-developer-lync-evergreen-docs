---
title: Class library changes
TOCTitle: Class library changes
ms:assetid: e0f5e5d8-b307-4abb-a472-ebe74b5ef638
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439202(v=office.15)
ms:contentKeyID: 57101303
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Class library changes

Learn about updates to the Microsoft Lync Server 2013 Persistent Chat API class library.


**Applies to:** Lync 2013 | Lync Server 2013

## Class library

The following list shows the changes of the Lync Server 2013 Persistent Chat API types that are introduced in the current release.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft.Rtc.Collaboration.GroupChat.ChatRoomCategorySettings</p></td>
<td><p>This type is removed.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266914(v=office.15)">ChatMessage</a></p></td>
<td><p>The following members are added to support RTF content in chat rooms:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj266901(v=office.15)">FormattedRtfMessageParts</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267312(v=office.15)">MessageRtfContent</a></p></li>
</ul>
<p>To provide RTF content, the Microsoft Lync Server 2013 Persistent Chat API application must also provide the corresponding plain text content to support legacy chat clients.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267575(v=office.15)">ChatRoom</a></p></td>
<td><p>The following members are removed from a room as the result of the refactoring of the properties of categories and rooms due to the simplification of the chat room administration and management:</p>
<ul>
<li><p>AllowFileUpload</p></li>
<li><p>CreateNewMemberList</p></li>
<li><p>LogChatHistory</p></li>
<li><p>Topic</p></li>
</ul>
<p>Some of these properties are no longer needed due to the flattening of the category hierarchy and some are now exposed only on a category. The Topic property is no longer present on a chat room.</p>
<p>The following member has types changed:</p>
<ul>
<li><p><strong>SendInvitationsToMembers()</strong></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>ChatRoomInformation</strong></p></td>
<td><p>The following member has types changed:</p>
<ul>
<li><p><strong>SendInvitationsToMembers()</strong>. The property type changed from bool to <strong>ChatRoomInvitationSetting</strong>.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266932(v=office.15)">ChatRoomInvitationSetting</a></p></td>
<td><p>New type introduced in the current release.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266929(v=office.15)">ChatRoomRole</a></p></td>
<td><p>The following member is added:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj266929(v=office.15)">Creator</a></p></li>
</ul>
<p>A creator has privileges to create rooms within a category. An end user cannot change an existing room to another category.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267572(v=office.15)">ChatRoomPrivacy</a></p></td>
<td><p>This is a new type.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj265925(v=office.15)">ChatRoomSession</a></p></td>
<td><p>The following members are added:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj265980(v=office.15)">BeginSendChatMessage(FormattedOutboundChatMessage, String, AsyncCallback, Object)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj266399(v=office.15)">BeginSendChatMessage(String, Boolean, String, AsyncCallback, Object)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj266940(v=office.15)">BeginSendChatMessage(String, String, String, Boolean, AsyncCallback, Object)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj265952(v=office.15)">BeginSendChatMessage(String, String, AsyncCallback, Object)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267914(v=office.15)">Description</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267250(v=office.15)">IsFilePostAllowed</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj265910(v=office.15)">IsInvite</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267253(v=office.15)">IsLogged</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267214(v=office.15)">VisibleOnlyToMembers</a></p></li>
</ul>
<p>The following member is removed from this type:</p>
<ul>
<li><p>Topic</p></li>
</ul>
<p>Chat room description can be used to add additional information to describe the topic of a chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267618(v=office.15)">ChatRoomSettings</a></p></td>
<td><p>The following members are removed:</p>
<ul>
<li><p>AllowFileUpload</p></li>
<li><p>CreateNewMemberList</p></li>
<li><p>LogChatHistory</p></li>
<li><p>Topic</p></li>
</ul>
<p>The following member has types changed:</p>
<ul>
<li><p><strong>SendInvitationsToMembers()</strong>. The property type changed from bool to <strong>ChatRoomInvitationSetting</strong>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267241(v=office.15)">ChatRoomSnapshot</a></p></td>
<td><p>The following member is removed:</p>
<ul>
<li><p>Topic</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267628(v=office.15)">ChatRoomSummary</a></p></td>
<td><p>The following member is added:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267637(v=office.15)">Description</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267567(v=office.15)">PersistentChatEndpoint</a></p></td>
<td><p>The following member is removed:</p>
<ul>
<li><p>GroupChatEndpoint..ctor(Uri, LocalEndpoint, string)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267188(v=office.15)">PersistentChatServerConfiguration</a></p></td>
<td><p>The following members are added:</p>
<ul>
<li><p><strong>DisplayName()</strong>. This is the name of the Persistent Chat pool that can be used to disambiguate a room.</p></li>
<li><p><strong>RoomManagementUrl()</strong>. This is used to point to a custom room management page in which specific business rules and conventions can be enforced or specified users can be directed through a given workflow.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267628(v=office.15)">ChatRoomSummary</a></p></td>
<td><p>The following member is new.</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267637(v=office.15)">Description</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266890(v=office.15)">PersistentChatServices</a></p></td>
<td><p>The following member is removed:</p>
<ul>
<li><p>CategoryManagementServices</p></li>
</ul>
<p>The following member is modified:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267603(v=office.15)">BeginBrowseChatRoomsByCriteria(String, Boolean, Boolean, Boolean, AsyncCallback, Object)</a></p></li>
</ul>
<p>The following members are added:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj266916(v=office.15)">BeginBrowseChatRoomsIManage(AsyncCallback, Object, UInt32)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267602(v=office.15)">BeginBrowseMyChatRooms(AsyncCallback, Object, UInt32)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267330(v=office.15)">EndBrowseChatRoomsIManage(IAsyncResult)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267862(v=office.15)">EndBrowseMyChatRooms(IAsyncResult)</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267896(v=office.15)">InheritedChatRoomInviteProperty</a></p></td>
<td><p>This is a new type.</p></td>
</tr>
<tr class="odd">
<td><p>InheritedChatRoomProperty</p></td>
<td><p>This type is removed.</p></td>
</tr>
<tr class="even">
<td><p>ChatRoomCategoryInformation</p></td>
<td><p>This type is removed from the <a href="https://msdn.microsoft.com/en-us/library/jj267343(v=office.15)">Microsoft.Rtc.Collaboration.PersistentChat.Management</a> namespace.</p></td>
</tr>
<tr class="odd">
<td><p>ChatRoomCategoryManagementServices</p></td>
<td><p>This type is removed from the <a href="https://msdn.microsoft.com/en-us/library/jj267343(v=office.15)">Microsoft.Rtc.Collaboration.PersistentChat.Management</a> namespace.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266922(v=office.15)">ChatRoomInformation</a></p></td>
<td><p>The following members are removed:</p>
<ul>
<li><p>AllowFileUpload</p></li>
<li><p>CreateNewMemberList</p></li>
<li><p>LogChatHistory</p></li>
<li><p>Topic</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Rtc.Collaboration.GroupChat.Management.GroupChatAddInInformation</p></td>
<td><p>This type is removed.</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Rtc.Collaboration.GroupChat.Management.GroupChatAddInSettings</p></td>
<td><p>This type is removed.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj265913(v=office.15)">PersistentChatRoleDescriptor</a></p></td>
<td><p>The following member is removed:</p>
<ul>
<li><p>InheritedFrom</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>GroupChatFederatedUser</p></td>
<td><p>Removed from the <a href="https://msdn.microsoft.com/en-us/library/jj267343(v=office.15)">Microsoft.Rtc.Collaboration.PersistentChat.Management</a> namespace, as federation is no longer supported in the Microsoft Lync Server 2013 Persistent Chat SDK.</p></td>
</tr>
<tr class="odd">
<td><p>GroupChatFederatedUserGroup</p></td>
<td><p>Removed from the <a href="https://msdn.microsoft.com/en-us/library/jj267343(v=office.15)">Microsoft.Rtc.Collaboration.PersistentChat.Management</a> namespace</p></td>
</tr>
<tr class="even">
<td><p>GroupChatFederatedUserGroupInformation</p></td>
<td><p>Removed from the <a href="https://msdn.microsoft.com/en-us/library/jj267343(v=office.15)">Microsoft.Rtc.Collaboration.PersistentChat.Management</a> namespace</p></td>
</tr>
<tr class="odd">
<td><p>GroupChatFederatedUserInformation</p></td>
<td><p>Removed from the <a href="https://msdn.microsoft.com/en-us/library/jj267343(v=office.15)">Microsoft.Rtc.Collaboration.PersistentChat.Management</a> namespace</p></td>
</tr>
<tr class="even">
<td><p>GroupChatFederatedUserSettings</p></td>
<td><p>Removed from the <a href="https://msdn.microsoft.com/en-us/library/jj267343(v=office.15)">Microsoft.Rtc.Collaboration.PersistentChat.Management</a> namespace</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266388(v=office.15)">PersistentChatPrincipal</a></p></td>
<td><p>The following members are removed from the type.</p>
<ul>
<li><p>ArePermissionsInherited</p></li>
<li><p>CanUploadFiles</p></li>
<li><p>IsChatRoomAdministrator</p></li>
<li><p>IsUserAdministrator</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Microsoft.Rtc.Collaboration.GroupChat.Management.GroupChatPrincipalInformation</p></td>
<td><p>This type is removed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PersistentChatUserAdministrationServices</strong></p></td>
<td><p>The following members are removed from the type.</p>
<ul>
<li><p>BeginCreateFederatedUser</p></li>
<li><p>BeginCreateFederatedUserGroup</p></li>
<li><p>BeginDeleteFederatedUserGroup</p></li>
<li><p>BeginGetFederatedUser</p></li>
<li><p>BeginGetFederatedUserGroup</p></li>
<li><p>BeginGetFederatedUserGroups</p></li>
<li><p>BeginGetFederatedUsers</p></li>
<li><p>BeginGetGroupChatAdministrators</p></li>
<li><p>BeginMoveFederatedUser</p></li>
<li><p>BeginUpdateUserOrGroupInformation</p></li>
<li><p>EndCreateFederatedUser</p></li>
<li><p>EndCreateFederatedUserGroup</p></li>
<li><p>EndDeleteFederatedUserGroup</p></li>
<li><p>EndGetFederatedUser</p></li>
<li><p>EndGetFederatedUserGroups</p></li>
<li><p>EndGetFederatedUsers</p></li>
<li><p>EndGetGroupChatAdministrators</p></li>
<li><p>EndMoveFederatedUser</p></li>
<li><p>EndUpdateUserOrGroupInformation</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Microsoft.Rtc.Collaboration.GroupChat.Management.GroupChatUserGroupInformation</p></td>
<td><p>This type is removed.</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Rtc.Collaboration.GroupChat.Management.GroupChatUserInformation</p></td>
<td><p>This type is removed.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Updated object model](updated-object-model.md)

[What's new in Lync Server 2013 Persistent Chat SDK](what-s-new-in-lync-server-2013-persistent-chat-sdk.md)

