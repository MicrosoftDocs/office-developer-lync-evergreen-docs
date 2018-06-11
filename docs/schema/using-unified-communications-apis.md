---
title: Using Unified Communications APIs
TOCTitle: Using Unified Communications APIs
ms:assetid: 5d55eeca-721c-4668-a94f-17906b9e2087
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454644(v=office.15)
ms:contentKeyID: 57093179
ms.date: 02/11/2016
mtps_version: v=office.15
---

# Using Unified Communications APIs


**Applies to:** Lync 2013 | Lync Server 2013

In a Microsoft Lync Server 2013 deployment, a unified communications application can use the following unified communications APIs to enable enhanced presence.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Microsoft Lync 2013 Controls</p></td>
<td><p>This API supports drag-and-drop controls that expose limited enhanced presence-related features of Microsoft Lync 2013. All presence features are exposed as properties of the presence controls. A Microsoft Silverlight browser or a Microsoft Windows Presentation Framework (WPF) application can use these controls to leverage the supported Lync presence features. Presence controls:</p>
<dl>
<dt><strong>PresenceIndicator control</strong></dt>
<dd><p>This control can be used to display the availability and activity string of a specified contact. It can also be used to determine and configure how the presence photo appears in the UI.</p>
</dd>
<dt><strong>ContactCard, ContactList, and CustomContactList controls</strong></dt>
<dd><p>These controls are used to show basic or detailed contact information of a specified contact, to manage a contact list.</p>
</dd>
<dt><strong>ContactSearchInputBox and ContactSearchResultList controls</strong></dt>
<dd><p>These controls are used to search users by alias, names, keywords, or phone number.</p>
</dd>
</dl>
<p>For more information about how to use the controls to enable enhanced presence, see <a href="../desktop/lync-2013-sdk-documentation.md">Lync 2013 SDK documentation</a>.</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Lync 2013 API</p></td>
<td><p>This is the automation API for Microsoft Lync 2013. It allows an application to leverage and extend the enhanced presence features as well as other collaboration functionality supported by Lync 2013. As with the Lync 2013 Controls, the enhanced presence data is encapsulated by the API objects and accessible through the properties on these objects. Lync 2013 API supports more enhanced presence features supported by Lync 2013 than the Lync 2013 Controls does. For more information about how to use the controls to enable enhanced presence, see <a href="../desktop/lync-2013-sdk-documentation.md">Lync 2013 SDK documentation</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Unified Communications Managed API 4.0</p></td>
<td><p>This API is more versatile in terms of the feature support. It can be used to build a full-fledged unified communications client, middle-tier, or server application. A UCMA application has the full control of the enhanced presence features, including grammar-based and grammar-free presence publication, custom container semantics, and custom presence categories. The general enhanced presence programming examples presented in this documentation are created using this API.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Programming with Enhanced Presence](programming-with-enhanced-presence.md)

