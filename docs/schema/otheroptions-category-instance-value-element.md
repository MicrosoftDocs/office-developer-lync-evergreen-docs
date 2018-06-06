---
title: otherOptions category instance value element
TOCTitle: otherOptions category instance value element
ms:assetid: f4cc6abc-834f-4804-b284-283357c909ee
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454755(v=office.15)
ms:contentKeyID: 57093642
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# otherOptions category instance value element


_**Applies to:** Lync Server 2013_

Contains the miscellaneous options that can be set by the user using Microsoft Lync 2013.

``` xml
<otherOptions xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    majorVersion="xs:unsignedInt"
    minorVersion="xs:unsignedInt"
    [anyAttr]="any" 
    xmlns="http://schemas.microsoft.com/2006/09/sip/options/otherOptions">
    <permissions>element sequence</permissions>
    <voiceMailLastAccessTimestamp>xs:string</voiceMailLastAccessTimestamp>
    <missedConversationLastAccessTimestamp>xs:string</missedConversationLastAccessTimestamp>
    <privacyModeUserSelection>privacyModeUserSelectionEnumEx</privacyModeUserSelection>
    <currentPrivacyMode>privacyModeEnumEx</currentPrivacyMode>
    <lastQueryPrivacyEnabled>xs:boolean</lastQueryPrivacyEnabled>
    <publishEndpointLocation>xs:boolean</publishEndpointLocation>
    <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <[any] xmlns="http://schemas.microsoft.com/2006/09/sip/options/otherOptions">any element for a schema extension</[any]>
    <ct:end/>
    <ct:extension>
        <[any] xmlns="any_namespace">any element for custom extension</[any]>
    </ct:extension>
</otherOptions>
```

otherOptionsType

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Attribute</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify the major version number for the publication of this element.</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify the minor version number for the publication of this element.</p></td>
</tr>
<tr class="odd">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name in any namespace.</p></td>
</tr>
</tbody>
</table>


#### Child elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Occurrence</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="alerts-alertswhendonotdisturb-element.md">alerts/alertsWhenDoNotDisturb element</a></p></td>
<td><p>1</p></td>
<td><p>A sequence of XML elements specifying the permissions configuration on Lync 2013.</p></td>
</tr>
<tr class="even">
<td><p><a href="alerts-notifyadditiontocontactlist-element.md">alerts/notifyAdditionToContactList element</a></p></td>
<td><p>0 or 1</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><a href="alerts-showmessagetextforincomingconversation-element.md">alerts/showMessageTextForIncomingConversation element</a></p></td>
<td><p>0 or 1</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>privacyModeUserSelection</p></td>
<td><p>0 or 1</p></td>
<td><p>User selection of the privacy mode.</p>
<p>New in the Microsoft Lync Server 2010 release.</p></td>
</tr>
<tr class="odd">
<td><p>currentPrivacyMode</p></td>
<td><p>0 or 1</p></td>
<td><p>Current privacy mode</p>
<p>New in the Lync Server 2010 release.</p></td>
</tr>
<tr class="even">
<td><p>lastQueryPrivacyEnabled</p></td>
<td><p>0 or 1</p></td>
<td><p>A Boolean flag to indicate whether the last query of privacy is enabled or not.</p>
<p>New in the Lync Server 2010 release.</p></td>
</tr>
<tr class="odd">
<td><p>publishEndpointLocation</p></td>
<td><p>0 or 1</p></td>
<td><p>A Boolean flag to indicate whether to publish the endpoint location or not.</p>
<p>New in the Lync Server 2010 release.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-dependent custom extension to this element.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A marker to begin a version-dependent schema extension.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Custom element of any name in the same namespace describing a schema extension to this element. This element must be enclosed between a delimiter element and an end element or between a two delimiter elements.</p></td>
</tr>
<tr class="odd">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The marker to end all the schema extensions.</p></td>
</tr>
</tbody>
</table>


#### Parent elements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>None</p></td>
<td><p>This is a top-level element as the value of an enhanced presence data of the alerts category name.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/options/otherOptions</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>options-otherOptions</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>options-otherOptions.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Category instance elements for presence](category-instance-elements-for-presence.md)

