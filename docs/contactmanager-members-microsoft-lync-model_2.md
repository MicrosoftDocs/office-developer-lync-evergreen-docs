---
title: ContactManager members (Microsoft.Lync.Model)
TOCTitle: ContactManager members
ms:assetid: AllMembers.T:Microsoft.Lync.Model.ContactManager_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager_di_3_uc_ocs14mreflyncwpf_members(v=office.15)
ms:contentKeyID: 48588633
ms.date: 07/28/2014
mtps_version: v=office.15
---

# ContactManager members

Include protected members  
Include inherited members  

The contact manager class is used to add, remove, and update contacts and their properties. The contact manager is also used to access Lync contact list groups.

The [ContactManager](contactmanager-class-microsoft-lync-model_2.md) type exposes the following members.

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
<td><a href="contactmanager-groups-property-microsoft-lync-model_2.md">Groups</a></td>
<td>Returns the group collection.</td>
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
<td><a href="contactmanager-beginaddgroup-method-string-asynccallback-object-microsoft-lync-model_2.md">BeginAddGroup(String, AsyncCallback, Object)</a></td>
<td>Adds a new custom group to the group list.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-beginaddgroup-method-distributiongroup-asynccallback-object-microsoft-lync-model_2.md">BeginAddGroup(DistributionGroup, AsyncCallback, Object)</a></td>
<td>Adds a distribution group to the group list.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-beginlookup-method-microsoft-lync-model_2.md">BeginLookup</a></td>
<td>Looks up a contact or a distribution group by entryid, sip address, email address, display name, etc..</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-beginremovecontactfromallgroups-method-microsoft-lync-model_2.md">BeginRemoveContactFromAllGroups</a></td>
<td>Removes a contact from all groups except distribution groups.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-beginremovegroup-method-microsoft-lync-model_2.md">BeginRemoveGroup</a></td>
<td>Removes a group from the group list.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-beginsearch-method-string-asynccallback-object-microsoft-lync-model_2.md">BeginSearch(String, AsyncCallback, Object)</a></td>
<td>Begins to search for contacts or distribution groups matching a specified search string. Results of the search are returned in the System.AsyncCallback you pass in the contactsAndGroupsCallback argument.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-beginsearch-method-string-searchproviders-searchfields-searchoptions-uint32-asynccallback-object-microsoft-lync-model_2.md">BeginSearch(String, SearchProviders, SearchFields, SearchOptions, UInt32, AsyncCallback, Object)</a></td>
<td>Searches for contacts and distribution groups that match the given search criteria.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/2ch65xad">CreateObjRef</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-createsubscription-method-microsoft-lync-model_2.md">CreateSubscription</a></td>
<td>Creates a Subscription object that can be used for batching subscriptions or queries.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-endaddgroup-method-microsoft-lync-model_2.md">EndAddGroup</a></td>
<td>Adds a new custom group to the group list.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-endlookup-method-microsoft-lync-model_2.md">EndLookup</a></td>
<td>Looks up a contact or a distribution group by entryid, sip address, email address, display name, etc..</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-endremovecontactfromallgroups-method-microsoft-lync-model_2.md">EndRemoveContactFromAllGroups</a></td>
<td>Removes a contact from all groups except distribution groups.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-endremovegroup-method-microsoft-lync-model_2.md">EndRemoveGroup</a></td>
<td>Removes a group from the group list.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-endsearch-method-microsoft-lync-model_2.md">EndSearch</a></td>
<td>Searches for contacts and distribution groups that match the given search criteria.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/bsc2ak47">Equals</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="contactmanager-finalize-method-microsoft-lync-model_1.md">Finalize</a></td>
<td>(Overrides <strong>UCWFullFinalize()</strong>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-getcontactbyuri-method-microsoft-lync-model_2.md">GetContactByUri</a></td>
<td>Finds or creates a new contact using the contact URI.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-getexpertsearchquerystring-method-microsoft-lync-model_2.md">GetExpertSearchQueryString</a></td>
<td>Gets the search query string used for expert search.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/zdee4b3y">GetHashCode</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/c6y7316f">GetLifetimeService</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-getsearchfields-method-microsoft-lync-model_2.md">GetSearchFields</a></td>
<td>Gets the supported search fields.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-getsearchproviderid-method-microsoft-lync-model_2.md">GetSearchProviderID</a></td>
<td>Gets the ID of a search provider.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="contactmanager-getsearchproviderstatus-method-microsoft-lync-model_2.md">GetSearchProviderStatus</a></td>
<td>Gets the search provider status.</td>
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
<td><a href="contactmanager-groupadded-event-microsoft-lync-model_2.md">GroupAdded</a></td>
<td>Occurs when a group is added.</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="contactmanager-groupremoved-event-microsoft-lync-model_2.md">GroupRemoved</a></td>
<td>Occurs when a group is removed.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="contactmanager-searchproviderstatechanged-event-microsoft-lync-model_2.md">SearchProviderStateChanged</a></td>
<td>Occurs when the status of a search provider changes.</td>
</tr>
</tbody>
</table>


Top

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

