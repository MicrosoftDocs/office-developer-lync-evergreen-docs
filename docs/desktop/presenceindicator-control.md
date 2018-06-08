---
title: PresenceIndicator control
TOCTitle: PresenceIndicator control
ms:assetid: 66bf9c40-6b68-4d31-aac5-ca7f780b889e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945547(v=office.15)
ms:contentKeyID: 51541356
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# PresenceIndicator control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013PresenceIndicator control.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Control overview<br />
Quick connect menu<br />
Members<br />
Code example<br />
Additional resources</p></td>
<td></td>
</tr>
</tbody>
</table>

## Control overview

The [PresenceIndicator](https://msdn.microsoft.com/en-us/library/hh345947\(v=office.15\)) control displays one of several icons that indicate the presence of a given user. It is a stand-alone control representing a single contact and enables access to the quick connect menu and the contact card for the user. The control also can display a photo for the given user. The following images display different options for the PhotoDisplayMode property. When the Source property is not set or when no photo is available, a stock silhouette image appears in the UI as shown.

![PresenceIndicator Control](images/JJ933141.PresenceIndicatorControl(Office.15).png "PresenceIndicator Control")

![PresenceIndicator Control](images/JJ933141.PresenceIndicator_large_rtm(Office.15).png "PresenceIndicator Control")

## Quick connect menu

The control reacts to two user actions: hover and click. When a user hovers over the icon, after about one second the quick connect menu appears. The quick connect menu displays the contact’s presence, starts IM, email, or audio calls and can be expanded to show detailed contact information. The quick connect menu disappears if it is not used. The user can keep the quick connect menu open by pinning it.

## Members

Notable PresenceIndicator control public properties and events relating to unified communications appear in the following table. For information about other properties and events, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/en-us/library/jj933088\(v=office.15\)).

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property or event</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363511(v=office.15)">Source</a> property</p></td>
<td><p>Gets or sets the contact to display. Valid types include the <a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Contact</a> object, <a href="https://msdn.microsoft.com/en-us/library/jj293432(v=office.15)">DistributionGroup</a> object, and <a href="http://go.microsoft.com/fwlink/?linkid=131086%26clcid=0x409">String</a>.</p>
<ul>
<li><p>If the value is a string that does not contain the sip: or tel: prefix, the control performs a search, using the string specified as a search criteria, and loads the first contact in the result set matching the specified string. This behavior is not deterministic and yields the slowest performance.</p></li>
<li><p>If the value is a SIP URI string qualified by the sip: or tel: prefix, the contact is loaded using an exact match of the specified URI. This behavior is deterministic and yields better performance.</p></li>
<li><p>If the value is a Contact or DistributionGroup object, it is used without changes. This behavior is deterministic and yields the best performance.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh346421(v=office.15)">ActivityStatus</a> property</p></td>
<td><p>Gets the presence status string for the contact. For example, In a meeting or Away. For groups, this is an empty string.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh345805(v=office.15)">DisplayName</a> property</p></td>
<td><p>Gets the contact’s display name.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363342(v=office.15)">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about the use of contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh346458(v=office.15)">Model</a> property</p></td>
<td><p>Reserved for internal use. When you edit templates, this property may appear in XAML text. To preserve control functionality, it should remain static.</p></td>
</tr>
<tr class="even">
<td><p>AvailabilityState property</p></td>
<td><p>Gets an enumerated value that represents the contact’s availability. The type is a <strong>ContactAvailability</strong> enumeration. Possible values:</p>
<ul>
<li><p>Invalid</p></li>
<li><p>None</p></li>
<li><p>Free</p></li>
<li><p>FreeIdle</p></li>
<li><p>Busy</p></li>
<li><p>BusyIdle</p></li>
<li><p>DoNotDisturb</p></li>
<li><p>TemporarilyAway</p></li>
<li><p>Away</p></li>
<li><p>Offline</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh345520(v=office.15)">HoverAction</a> property</p></td>
<td><p>Gets or sets an enumeration value that determines the contact card display mode when the cursor hovers over the presence icon. The default value is <strong>ShowContactBrief</strong>.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363323(v=office.15)">SingleClickAction</a> property</p></td>
<td><p>Gets or sets an enumeration value that determines the contact card display mode after the presence icon is clicked. The default value is <strong>ShowContactDetails</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>PhotoDisplayMode property</p></td>
<td><p>Gets or sets an enumeration value that determines the presence photo display mode. The default value is <strong>Hidden</strong>.</p></td>
</tr>
</tbody>
</table>

## Code example

The following sample code is for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF).

```xaml
<StackPanel>
  <controls:PresenceIndicator Source="sip:mary@contoso.com"/>
</StackPanel>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

