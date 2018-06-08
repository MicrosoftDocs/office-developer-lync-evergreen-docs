---
title: Presence samples
TOCTitle: Presence samples
ms:assetid: 87a76d00-13fb-462c-8d1c-2d68ad10807b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933099(v=office.15)
ms:contentKeyID: 50877231
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Presence samples

![Code sample topic](images/JJ937254.mod_icon_codesample_long(Office.15).png "Code sample topic")

Learn about the presence-related quick-start samples that are installed with Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Presence samples<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Presence samples

The quick-start samples in the following table show how to publish and get presence for a contact by using presence controls or objects in the Lync 2013 API object model.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Application</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MyNotebox</p></td>
<td><p>Populates a page with a <a href="https://msdn.microsoft.com/en-us/library/hh346137(v=office.15)">Microsoft.Lync.Controls.MyNoteBox</a> control and displays the signed-in user’s display name and personal note in a text entry control.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\MyNoteBoxDesktop</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\MyNoteBoxSilverlight</p></li>
</ul>
<p>Download the sample from Code Gallery at the following locations:</p>
<ul>
<li><p>WPF sample location: <a href="http://code.msdn.microsoft.com/lync-2013-set-a-personal-193337c9">Lync 2013: Set a personal note in a WPF app by using a personal note control</a></p></li>
<li><p>Silverlight sample location: <a href="http://code.msdn.microsoft.com/lync-2013-set-a-personal-e1a0899f">Lync 2013: Set a personal note in a Silverlight app</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>MyPresenceChooser</p></td>
<td><p>Populates a window with a <a href="https://msdn.microsoft.com/en-us/library/hh379434(v=office.15)">Microsoft.Lync.Controls.MyPresenceChooser</a> control that lets a user choose a presence activity. The resulting availability state is displayed in a text block in the window.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\MyPresenceChooserDesktop</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\MyPresenceChooserSilverlight</p></li>
</ul>
<p>Download the sample from Code Gallery at the following locations:</p>
<ul>
<li><p>WPF sample location: <a href="http://code.msdn.microsoft.com/lync-2013-set-presence-6ed5f212">Lync 2013: Set presence indicator and view current activity in a WPF app</a></p></li>
<li><p>Silverlight sample location: <a href="http://code.msdn.microsoft.com/lync-2013-set-presence-5a7b7727">Lync 2013: Set presence indicator and view current activity in a Silverlight app</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>MyStatusArea</p></td>
<td><p>Populates a window with a <a href="https://msdn.microsoft.com/en-us/library/hh363503(v=office.15)">Microsoft.Lync.Controls.MyStatusArea</a> control that lets a user choose a presence activity and enter a personal note. Three text blocks on the page are bound to <strong>MyStatusArea</strong> control properties for user display name, availability state, and personal note. The text value of these text blocks are automatically updated when the corresponding properties of the <strong>MyStatusControl</strong> change.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\MyStatusAreaDesktop</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\MyStatusAreaSilverlight</p></li>
</ul>
<p>Download the sample from Code Gallery at the following locations:</p>
<ul>
<li><p>WPF sample location: <a href="http://code.msdn.microsoft.com/lync-2013-display-contact-81931a5f">Lync 2013: Display contact cards in a WPA app using a MyStatusArea control</a></p></li>
<li><p>Silverlight sample location: <a href="http://code.msdn.microsoft.com/lync-2013-display-contact-15ccbfc5">Lync 2013: Display contact cards in a Silverlight app</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>PresenceIndicator</p></td>
<td><p>Populates a list on a page with three <a href="https://msdn.microsoft.com/en-us/library/hh345947(v=office.15)">Microsoft.Lync.Controls.PresenceIndicator</a> instances. The user can hover a mouse pointer over any of the presence indicators to display a contact card a user. The <a href="https://msdn.microsoft.com/en-us/library/hh363511(v=office.15)">ContactBase.Source</a> property for each control instance is set by the sample application.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\PresenceIndicatorDesktop</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\PresenceIndicatorSilverlight</p></li>
</ul>
<p>Download the sample from Code Gallery at the following locations:</p>
<ul>
<li><p>WPF sample location: <a href="http://code.msdn.microsoft.com/lync-2013-use-a-wpf-4541b201">Lync 2013: Use a WPF control to indicate the presence of participants</a></p></li>
<li><p>Silverlight sample location: <a href="http://code.msdn.microsoft.com/lync-2013-use-a-silverlight-18a585be">Lync 2013: Use a Silverlight control to indicate the presence of participants</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-use-the-lync-47ded7b4">Presence publication</a></p></td>
<td><p>Retrieve and publish information of the Self contact (the currently signed-in user) by using classes, enumerations, events, and methods of the Lync 2013 API. It also shows how to sign in to Lync using the credentials of the active user. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj274980(v=office.15)">Microsoft.Lync.Model.LyncClient</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Microsoft.Lync.Model.Contact</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj277683(v=office.15)">Microsoft.Lync.Model.Self</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj293978(v=office.15)">Microsoft.Lync.Model.ContactAvailability</a> enumeration</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj275543(v=office.15)">Contact.ContactInformationChanged</a> event</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj294012(v=office.15)">Contact.GetContactInformation</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj278107(v=office.15)">Self.BeginPublishContactInformation</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj274512(v=office.15)">LyncClient.BeginSignIn</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj277581(v=office.15)">LyncClient.BeginSignOut</a> method</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%\</em>Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\PresencePublication</p></td>
</tr>
</tbody>
</table>

## See also

  - [Code samples: Lync SDK](code-samples-lync-sdk.md)

