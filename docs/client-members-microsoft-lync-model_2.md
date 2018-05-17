---
title: Client members (Microsoft.Lync.Model)
TOCTitle: Client members
ms:assetid: AllMembers.T:Microsoft.Lync.Model.Client_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.client_di_3_uc_ocs14mreflyncwpf_members(v=office.15)
ms:contentKeyID: 48588562
ms.date: 07/28/2014
mtps_version: v=office.15
---

# Client members

Include protected members  
Include inherited members  

Abstract client class which represents the main entry point for the API. Represents the Lync client and provides access to conversations and contacts via their respective manager classes.

The [Client](client-class-microsoft-lync-model_2.md) type exposes the following members.

## Properties

<table>
<thead>
<tr class="header">
<th> </th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-contactmanager-property-microsoft-lync-model_2.md">ContactManager</a></td>
<td>Gets the contact group manager.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-conversationmanager-property-microsoft-lync-model_2.md">ConversationManager</a></td>
<td>Gets the conversation manager.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-roommanager-property-microsoft-lync-model_2.md">RoomManager</a></td>
<td>Gets the group chat room manager.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-self-property-microsoft-lync-model_2.md">Self</a></td>
<td>Gets the self Contact object representing the signed in user.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-settings-property-microsoft-lync-model_2.md">Settings</a></td>
<td>Gets the settings object.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-state-property-microsoft-lync-model_2.md">State</a></td>
<td>Gets the current platform state.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-uri-property-microsoft-lync-model_2.md">Uri</a></td>
<td>Gets the URI of the client.</td>
</tr>
</tbody>
</table>


Top

## Methods

<table>
<thead>
<tr class="header">
<th> </th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/2ch65xad">CreateObjRef</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/bsc2ak47">Equals</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="client-finalize-method-microsoft-lync-model_1.md">Finalize</a></td>
<td>(Overrides <strong>UCWFullFinalize()</strong>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/zdee4b3y">GetHashCode</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/c6y7316f">GetLifetimeService</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/dfwy45w9">GetType</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/zwt5tzck">InitializeLifetimeService</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/57ctke0a">MemberwiseClone()</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/ms131262">MemberwiseClone(Boolean)</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/7bxwbwt2">ToString</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
</tbody>
</table>


Top

## Events

<table>
<thead>
<tr class="header">
<th> </th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="client-statechanged-event-microsoft-lync-model_2.md">StateChanged</a></td>
<td>Occurs when the Client state changes.</td>
</tr>
</tbody>
</table>


Top

## See also

#### Reference

[Client class](client-class-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

