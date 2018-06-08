---
title: 'Beyond the basics: Enhanced presence'
TOCTitle: Enhanced presence
ms:assetid: 9eb537b8-c87c-47ec-aeb6-8850691cd44e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933150(v=office.15)
ms:contentKeyID: 50877287
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Beyond the basics: Enhanced presence

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about advanced enhanced presence concepts such as Lync 2013 contact privacy relationship administration and custom presence states in Microsoft Lync 2013 SDK.

**Last modified:** February 22, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Advanced features of enhanced presence<br />
In this section<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Advanced features of enhanced presence

A local user publishes a complete set of enhanced presence information, including name, business title, company name, business address, email address, state information, personal note, and personal telephone numbers. The local user also creates contact privacy relationships with other users to restrict the visibility of the published enhanced presence. A custom client Microsoft Lync 2013 API-based application that replaces a UI suppressed Lync 2013 client must be able to let a user define those privacy relationships with other users. The Lync 2013 API exposes the classes necessary to create a contact privacy relationship UI to replace the client feature.

You might need to create a set of custom user presence states that refine general presence states in a way that gives a more accurate view of a user’s availability. In addition, default activity can be customized to meet specific business or cultural requirements. Custom availability and custom activity values are defined by a Lync Server 2013 administrator but the publication and display logic for custom states is performed at the client level. The Lync 2013 API exposes the classes necessary to publish and display custom presence states.

## In this section

  - [Contact privacy relationship administration](contact-privacy-relationship-administration.md)

  - [Custom presence states](custom-presence-states.md)

## See also

  - [Beyond the basics in Lync 2013 SDK](beyond-the-basics-in-lync-2013-sdk.md)

  - [Core concepts: Enhanced presence](core-concepts-enhanced-presence.md)

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

