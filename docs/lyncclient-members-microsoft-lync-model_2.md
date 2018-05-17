---
title: LyncClient members (Microsoft.Lync.Model)
TOCTitle: LyncClient members
ms:assetid: AllMembers.T:Microsoft.Lync.Model.LyncClient_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.lyncclient_di_3_uc_ocs14mreflyncwpf_members(v=office.15)
ms:contentKeyID: 48588559
ms.date: 07/28/2014
mtps_version: v=office.15
---

# LyncClient members

Include protected members  
Include inherited members  

Implements the client class which represents the main entry point for the API. Represents the Lync client and provides access to conversations and contacts via their respective manager classes.

The [LyncClient](lyncclient-class-microsoft-lync-model_2.md) type exposes the following members.

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
<td><a href="lyncclient-capabilities-property-microsoft-lync-model_2.md">Capabilities</a></td>
<td>Determine whether ours is the preferred client for a capability.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-contactmanager-property-microsoft-lync-model_2.md">ContactManager</a></td>
<td>Gets the contact group manager. (Inherited from <a href="client-class-microsoft-lync-model_2.md">Client</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-conversationmanager-property-microsoft-lync-model_2.md">ConversationManager</a></td>
<td>Gets the conversation manager. (Inherited from <a href="client-class-microsoft-lync-model_2.md">Client</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="lyncclient-delegatorclients-property-microsoft-lync-model_2.md">DelegatorClients</a></td>
<td>Gets an array of IDelegatorClient objects.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="lyncclient-devicemanager-property-microsoft-lync-model_2.md">DeviceManager</a></td>
<td>Gets the device manager.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="lyncclient-insuppressedmode-property-microsoft-lync-model_2.md">InSuppressedMode</a></td>
<td>Returns true when in Full UI Suppression mode.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-roommanager-property-microsoft-lync-model_2.md">RoomManager</a></td>
<td>Gets the group chat room manager. (Inherited from <a href="client-class-microsoft-lync-model_2.md">Client</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-self-property-microsoft-lync-model_2.md">Self</a></td>
<td>Gets the self Contact object representing the signed in user. (Inherited from <a href="client-class-microsoft-lync-model_2.md">Client</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-settings-property-microsoft-lync-model_2.md">Settings</a></td>
<td>Gets the settings object. (Inherited from <a href="client-class-microsoft-lync-model_2.md">Client</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="lyncclient-signinconfiguration-property-microsoft-lync-model_2.md">SignInConfiguration</a></td>
<td>Gets the configuration manager.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-state-property-microsoft-lync-model_2.md">State</a></td>
<td>Gets the current platform state. (Inherited from <a href="client-class-microsoft-lync-model_2.md">Client</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="client-uri-property-microsoft-lync-model_2.md">Uri</a></td>
<td>Gets the URI of the client. (Inherited from <a href="client-class-microsoft-lync-model_2.md">Client</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="lyncclient-utilities-property-microsoft-lync-model_2.md">Utilities</a></td>
<td>Returns an instance of the Utilities class.</td>
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
<td><a href="lyncclient-begininitialize-method-microsoft-lync-model_2.md">BeginInitialize</a></td>
<td>Initializes LyncClient when the Lync is in Suppressed Mode. You do not call this method when Lync is not suppressed.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="lyncclient-beginshutdown-method-microsoft-lync-model_2.md">BeginShutdown</a></td>
<td>Starts the collaboration platform shutdown process.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="lyncclient-beginsignin-method-microsoft-lync-model_2.md">BeginSignIn</a></td>
<td>Starts the uc Client sign in process with a specific availability.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="lyncclient-beginsignout-method-microsoft-lync-model_2.md">BeginSignOut</a></td>
<td>Starts the uc Client sign out process.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="lyncclient-createapplicationregistration-method-microsoft-lync-model_2.md">CreateApplicationRegistration</a></td>
<td>Construct an application registration object used to register a Silverlight conversation window extension application.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/2ch65xad">CreateObjRef</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="lyncclient-endinitialize-method-microsoft-lync-model_2.md">EndInitialize</a></td>
<td>Ends the Initialize operation and unblocks program execution on the calling thread.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="lyncclient-endshutdown-method-microsoft-lync-model_2.md">EndShutdown</a></td>
<td>Starts the collaboration platform shutdown process.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="lyncclient-endsignin-method-microsoft-lync-model_2.md">EndSignIn</a></td>
<td>Starts the uc Client sign in process with a specific availability.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="lyncclient-endsignout-method-microsoft-lync-model_2.md">EndSignOut</a></td>
<td>Starts the uc Client sign out process.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/bsc2ak47">Equals</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="lyncclient-finalize-method-microsoft-lync-model_1.md">Finalize</a></td>
<td>(Overrides <a href="client-finalize-method-microsoft-lync-model_1.md">Client.Finalize()</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /><img src="images/Hh365030.static(Office.15).gif" title="Static member" alt="Static member" /></td>
<td><a href="lyncclient-getautomation-method-microsoft-lync-model_2.md">GetAutomation</a></td>
<td>Creates an instance of Automation and returns.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /><img src="images/Hh365030.static(Office.15).gif" title="Static member" alt="Static member" /></td>
<td><a href="lyncclient-getclient-method-microsoft-lync-model_2.md">GetClient</a></td>
<td></td>
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
<td><a href="http://msdn2.microsoft.com/en-us/library/dfwy45w9">GetType</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/zwt5tzck">InitializeLifetimeService</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/57ctke0a">MemberwiseClone()</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/ms131262">MemberwiseClone(Boolean)</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="odd">
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
<td><a href="lyncclient-capabilitieschanged-event-microsoft-lync-model_2.md">CapabilitiesChanged</a></td>
<td>Raised when the preferred capabilities changed</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="lyncclient-clientdisconnected-event-microsoft-lync-model_2.md">ClientDisconnected</a></td>
<td>Raised when Lync connection is broken.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="lyncclient-credentialrequested-event-microsoft-lync-model_2.md">CredentialRequested</a></td>
<td>Raised when a user credential is requested by a server such as the Lync server.</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="lyncclient-delegatorclientadded-event-microsoft-lync-model_2.md">DelegatorClientAdded</a></td>
<td>Raised when a new delegate endpoint is created.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="lyncclient-delegatorclientremoved-event-microsoft-lync-model_2.md">DelegatorClientRemoved</a></td>
<td>Raised when an existing delegate endpoint is released.</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="lyncclient-signindelayed-event-microsoft-lync-model_2.md">SignInDelayed</a></td>
<td>Raised when there is a delay in the SignIn/auto-recover process</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="client-statechanged-event-microsoft-lync-model_2.md">StateChanged</a></td>
<td>Occurs when the Client state changes. (Inherited from <a href="client-class-microsoft-lync-model_2.md">Client</a>.)</td>
</tr>
</tbody>
</table>


Top

## See also

#### Reference

[LyncClient class](lyncclient-class-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

