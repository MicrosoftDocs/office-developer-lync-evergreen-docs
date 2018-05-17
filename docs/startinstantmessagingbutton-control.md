---
title: StartInstantMessagingButton control
TOCTitle: StartInstantMessagingButton control
ms:assetid: 1bb7a96c-1fa2-41a4-8764-ca6cd917ab29
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945537(v=office.15)
ms:contentKeyID: 51541336
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# StartInstantMessagingButton control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 StartInstantMessagingButton control.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Control overview<br />
Members<br />
Code example<br />
Additional resources</p></td>
<td></td>
</tr>
</tbody>
</table>


## Control overview

Use the [StartInstantMessagingButton](startinstantmessagingbutton-class-microsoft-lync-controls_1.md) control in Microsoft Lync Control applications to enable the user to open a Microsoft Lync 2013 conversation window and start an IM conversation between the user who activated the control and another user specified by the Source property. The control can also start an IM conversation with a distribution group.

![StartInstantMessagingButton Control](images/JJ937255.StartInstantMessagingButtonControl(Office.15).png "StartInstantMessagingButton Control")

## Members

Notable StartInstantMessagingButton control public properties and events relating to unified communications appear in the following table. For information about other properties and events, see [Lync 2013 class libraries reference](lync-2013-class-libraries-reference.md).

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="contactbase-displayname-property-microsoft-lync-controls_1.md">DisplayName</a> property</p></td>
<td><p>Gets the display name of the currently signed-in user.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactbase-source-property-microsoft-lync-controls_1.md">Source</a> property</p></td>
<td><p>Gets or sets the contact to use. Valid types include the <a href="contact-class-microsoft-lync-model_2.md">Contact</a> object, <a href="distributiongroup-class-microsoft-lync-model-group_2.md">DistributionGroup</a> object, and <a href="http://go.microsoft.com/fwlink/?linkid=131086%26clcid=0x409">String</a>.</p>
<ul>
<li><p>If the value is a string that does not contain the sip: or tel: prefix, the control performs a search, using the string specified as a search criteria, and loads the first contact in the result set matching the specified string. This behavior is not deterministic and yields the slowest performance.</p></li>
<li><p>If the value is a SIP URI string qualified by the sip: or tel: prefix, the contact is loaded using an exact match of the specified URI. This behavior is deterministic and yields better performance.</p></li>
<li><p>If the value is a Contact or DistributionGroup object, it is used without changes. This behavior is deterministic and yields the best performance.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="contactbase-contextualinformation-property-microsoft-lync-controls_1.md">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about the use of contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactbase-model-property-microsoft-lync-controls_1.md">Model</a> property</p></td>
<td><p>Reserved for internal use. This property may appear in XAML text when editing templates. To preserve control functionality, it should remain static.</p></td>
</tr>
</tbody>
</table>


## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

``` xaml
<StackPanel>
  <controls:StartInstantMessagingButton Source="sip:elise@contoso.com" />
</StackPanel>
```

## Additional resources

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

