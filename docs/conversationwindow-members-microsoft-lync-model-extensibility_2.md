---
title: ConversationWindow members (Microsoft.Lync.Model.Extensibility)
TOCTitle: ConversationWindow members
ms:assetid: AllMembers.T:Microsoft.Lync.Model.Extensibility.ConversationWindow_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindow_di_3_uc_ocs14mreflyncwpf_members(v=office.15)
ms:contentKeyID: 48592313
ms.date: 07/28/2014
mtps_version: v=office.15
---

# ConversationWindow members

Include protected members  
Include inherited members  

Represents a conversation window and exposes operations to manipulate the window of a conversation, including docking into a parent window.

The [ConversationWindow](conversationwindow-class-microsoft-lync-model-extensibility_2.md) type exposes the following members.

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
<td><a href="conversationwindow-conversation-property-microsoft-lync-model-extensibility_2.md">Conversation</a></td>
<td>Get the corresponding conversation object for this window.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-handle-property-microsoft-lync-model-extensibility_2.md">Handle</a></td>
<td>Returns the handle of the conversation window.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-height-property-microsoft-lync-model-extensibility_2.md">Height</a></td>
<td>The height of the conversation window in pixels.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-isdocked-property-microsoft-lync-model-extensibility_2.md">IsDocked</a></td>
<td>Is the window docked?</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-isfullscreen-property-microsoft-lync-model-extensibility_2.md">IsFullScreen</a></td>
<td>Is the window in full screen mode?</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-left-property-microsoft-lync-model-extensibility_2.md">Left</a></td>
<td>The horizontal position of the conversation window in pixels.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-parentwindow-property-microsoft-lync-model-extensibility_2.md">ParentWindow</a></td>
<td>Returns the handle of the parent window or control in which the conversation window is docked.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-properties-property-microsoft-lync-model-extensibility_2.md">Properties</a></td>
<td>Gets a collection of conversation window properties.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-state-property-microsoft-lync-model-extensibility_2.md">State</a></td>
<td>Gets the current state of the window.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-top-property-microsoft-lync-model-extensibility_2.md">Top</a></td>
<td>The vertical position of the conversation window in pixels.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversationwindow-width-property-microsoft-lync-model-extensibility_2.md">Width</a></td>
<td>The width of the conversation window in pixels.</td>
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
<td><a href="conversationwindow-beginopenextensibilitywindow-method-microsoft-lync-model-extensibility_2.md">BeginOpenExtensibilityWindow</a></td>
<td>Show the extensibility window for a registered application.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-caninvoke-method-microsoft-lync-model-extensibility_2.md">CanInvoke</a></td>
<td>Returns whether the given action is available</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-close-method-microsoft-lync-model-extensibility_2.md">Close</a></td>
<td>Closes the window.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-closeextensibilitywindow-method-microsoft-lync-model-extensibility_2.md">CloseExtensibilityWindow</a></td>
<td>Closes the extensibility window of the given application GUID.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/2ch65xad">CreateObjRef</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-dock-method-microsoft-lync-model-extensibility_2.md">Dock</a></td>
<td>Docks a conversation window inside a specified control. You can also dock a conversation window inside a form or a WPF WindowsFormsHostControl.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-endopenextensibilitywindow-method-microsoft-lync-model-extensibility_2.md">EndOpenExtensibilityWindow</a></td>
<td>Show the extensibility window for a registered application.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/bsc2ak47">Equals</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-exitfullscreen-method-microsoft-lync-model-extensibility_2.md">ExitFullScreen</a></td>
<td>Exits fullscreen.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="conversationwindow-finalize-method-microsoft-lync-model-extensibility_1.md">Finalize</a></td>
<td>(Overrides <strong>UCWFullFinalize()</strong>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-flashextensibilitywindow-method-microsoft-lync-model-extensibility_2.md">FlashExtensibilityWindow</a></td>
<td>Start or stop flashing the extensibility window of the given application GUID.</td>
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
<td><a href="conversationwindow-hidecontent-method-microsoft-lync-model-extensibility_2.md">HideContent</a></td>
<td>Hides the content</td>
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
<td><a href="conversationwindow-move-method-microsoft-lync-model-extensibility_2.md">Move</a></td>
<td>Move the window to new position.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-moveandresize-method-microsoft-lync-model-extensibility_2.md">MoveAndResize</a></td>
<td>Move And Resize the window with new position and size.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-resize-method-microsoft-lync-model-extensibility_2.md">Resize</a></td>
<td>Resize the window.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-showcontent-method-microsoft-lync-model-extensibility_2.md">ShowContent</a></td>
<td>Displays the content</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-showfullscreen-method-microsoft-lync-model-extensibility_2.md">ShowFullScreen</a></td>
<td>Fullscreens the ConversationWindow in it's current monitor</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/7bxwbwt2">ToString</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversationwindow-undock-method-microsoft-lync-model-extensibility_2.md">Undock</a></td>
<td>Undock the window.</td>
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
<td><a href="conversationwindow-actionavailabilitychanged-event-microsoft-lync-model-extensibility_2.md">ActionAvailabilityChanged</a></td>
<td>Raised when a conversation window information changes.</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversationwindow-informationchanged-event-microsoft-lync-model-extensibility_2.md">InformationChanged</a></td>
<td>Raised when a conversation window information changes.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversationwindow-needsattention-event-microsoft-lync-model-extensibility_2.md">NeedsAttention</a></td>
<td>Raised when the UI Window needs attention.</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversationwindow-needssizechange-event-microsoft-lync-model-extensibility_2.md">NeedsSizeChange</a></td>
<td>Raised when the UI Window size changes.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversationwindow-statechanged-event-microsoft-lync-model-extensibility_2.md">StateChanged</a></td>
<td>Raised when the conversation window state changes.</td>
</tr>
</tbody>
</table>


Top

## See also

#### Reference

[ConversationWindow class](conversationwindow-class-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

