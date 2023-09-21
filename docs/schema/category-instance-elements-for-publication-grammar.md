---
title: Category instance elements for publication grammar
TOCTitle: Category instance elements for publication grammar
ms:assetid: cfc395db-8463-4f77-9f8c-025b501bbf2e
ms:mtpsurl: https://msdn.microsoft.com/library/Dn438975(v=office.15)
ms:contentKeyID: 57094020
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Category instance elements for publication grammar

This section discusses the XML elements that are used to represent a container manifest and category publication manifest in an enhanced presence publication grammar.


**Applies to:** Lync 2013 | Lync Server 2013

Publication grammars are used to specify a set of rules for publishing presence category instances. There can be two kinds of rules in a publication grammar. One set of the rules dictates the containers that should be used and the access control entries that should be assigned to each container— a container manifest describes this set of rules in an XML element. The other set of rules specifies the category data that should be published to certain containers— a category publication manifest describes this set of rules in an XML element.

## In this section

The following table lists the XML elements used to represent a container manifest and a category publication manifest for a publication grammar.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>XML element</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="containermanifestlist-element.md">containerManifestList element</a></p></td>
<td><p>Holds a container manifest that specifies the containers that should be used in presence publications, and specifies access control for each container.</p></td>
</tr>
<tr class="even">
<td><p><a href="categorypublicationmanifest-element.md">categoryPublicationManifest element</a></p></td>
<td><p>Holds a category publication manifest that specifies the category data that should be published to certain containers.</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Category instance elements for presence](category-instance-elements-for-presence.md)

#### Concepts

[Get started with Enhanced Presence](get-started-with-enhanced-presence.md)

[Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md)

