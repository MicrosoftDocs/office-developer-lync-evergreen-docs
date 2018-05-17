---
title: mwi category instance value element
TOCTitle: mwi category instance value element
ms:assetid: 3169d257-280f-4075-afaf-b2a87931418e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454758(v=office.15)
ms:contentKeyID: 57093645
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# mwi category instance value element


_**Applies to:** Lync 2013 | Lync Server 2013_

Holds a Message Waiting Indictor (MWI) instance that is provisioned from Microsoft Exchange Server 2010.

``` xml
<mwi xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns="http://schemas.microsoft.com/2006/09/sip/mwi"
    majorVersion="xs:unsignedInt"
    minorVersion="xs:unsignedInt"
    anyAttr="any" 
    messageWaiting=”xs:boolean”
    unreadVoiceMailCount=”xs:unsignedInt”
    readVoiceMailCount=”xs:unsignedInt”>
    <[any]>any element in other namespace</any>
</mwi>
```

mwiType

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
<td><p>messageWaiting</p></td>
<td><p>Required attribute of the Boolean type to indicate whether a local user has new voice mails in their email account.</p></td>
</tr>
<tr class="even">
<td><p>unreadVoiceMailCount</p></td>
<td><p>Optional attribute of an unsigned integer type that specifies the number of unread voice mails in the local user’s email account.</p></td>
</tr>
<tr class="odd">
<td><p>readVoiceMailCount</p></td>
<td><p>Optional attribute of an unsigned integer type that specifies the number of read voice mails in the local user’s email account.</p></td>
</tr>
<tr class="even">
<td><p>majorVersion</p></td>
<td><p>Optional attribute that specifies schema-dependent major version information.</p></td>
</tr>
<tr class="odd">
<td><p>minorVersion</p></td>
<td><p>Optional attribute that specifies schema-dependent minor version information.</p></td>
</tr>
<tr class="even">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute that specifies a name from another namespace.</p></td>
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
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Custom element in any other namespace.</p></td>
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
<td><p>A top-level element as an enhanced presence category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

Message Waiting Indicator (MWI) is a Microsoft Exchange Unified Messaging feature that is supported by Microsoft Exchange 2010. It provides a notification mechanism to alert a user about the presence of new voice mails in the user’s Microsoft Outlook Inbox.

When a user receives a new voice mail, the Exchange Server sends out a SIP NOTIFY message that contains the MWI data for the specified user. After receiving the SIP message, Microsoft Lync Server 2013 publishes a private mwi category instance to the user’s Self container (ContainerId = 1). The publication is static and read-only. The instance ID of the published mwi category instance is 0. A local client cannot publish this category instance directly to the Self container, but can receive new and updated mwi category instances through self-subscription.

Exchange only sends MWI notifications to user accounts that are configured to use MWI. For information about how to enable MWI on Exchange, see [Understanding Message Waiting Indicator](http://technet.microsoft.com/en-us/library/dd298001.aspx).

## Example

The following XML code example shows a mwi category instance that specifies that the local user’s Outlook Inbox holds 10 voice mails, two of which have not been heard.

``` xml
<nt:mwi xmlns:nt="http://schemas.microsoft.com/2006/09/sip/mwi"
   messageWaiting=”true” unreadVoiceMailCount=”8” readVoiceMailCount=”2”>
</nt:mwi>
```

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/mwi</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>mwi</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>mwidata.xsd</p></td>
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

