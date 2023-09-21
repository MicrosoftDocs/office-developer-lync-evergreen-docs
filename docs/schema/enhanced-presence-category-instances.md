---
title: Enhanced Presence category instances
TOCTitle: Enhanced Presence category instances
ms:assetid: a599299f-f6c9-4a1e-8c50-46c53e376a72
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454622(v=office.15)
ms:contentKeyID: 57093012
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Enhanced Presence category instances


**Applies to:** Lync 2013 | Lync Server 2013

A particular piece of presence data corresponds to a category instance of the given category name. To indicate that a user is available while attending a meeting, a unified communications application can publish a presence state category instance containing the following presence state value.

    <state xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xsi:type="userState" 
           xmlns="http://schemas.microsoft.com/2006/09/sip/state">
       <availability>3500</availability>
       <activity>
          <custom LCID="1033">Meeting at 7/1234</custom>
       </activity>
    </state>

In addition to the presence data value, a category instance is also characterized by the following operational attributes:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category instance attribute</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Category Name</p></td>
<td><p>Identifies the type of presence data. This name is also the name of the XML element of a category instance.</p></td>
</tr>
<tr class="even">
<td><p>Instance ID</p></td>
<td><p>Identifies a specific category instance of a given name in a specified container. Instance IDs primarily serve to identify the presence sources of multiple instances of the same category name. It can also be used to distinguish different portions of the same presence data.</p></td>
</tr>
<tr class="odd">
<td><p>Container ID</p></td>
<td><p>Identifies the container where the category instance is published.</p></td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td><p>Used by the server to synchronize publishing of the category instance. A client must present a version number when publishing a category instance. The server is responsible for incrementing the version number of a category instance.</p></td>
</tr>
<tr class="odd">
<td><p>Expiry Type</p></td>
<td><p>Specifies the life-time type for the publication of a category instance.</p></td>
</tr>
<tr class="even">
<td><p>Expiration</p></td>
<td><p>Specifies the time when the publication of a category instance expires.</p></td>
</tr>
<tr class="odd">
<td><p>Publication Time</p></td>
<td><p>Specifies the time when a category instance was last published.</p></td>
</tr>
</tbody>
</table>


These category instance attributes are the metadata necessary for identifying, organizing, manipulating, and maintaining category instances throughout their life-cycle.

At the protocol level, category instances are transmitted as XML strings. The enhanced presence schemas discussed in this document apply to the data types of category instance values only. They do not define the syntax of the operational attributes of category instances.

The following XML string shows a list of contactCard category instances that are transmitted in a subscription.

    <categories xmlns="http://schemas.microsoft.com/2006/09/sip/categories" 
                uri="sip:john.doe@contoso.com">
       <category name="contactCard" instance="0" publishTime="2010-02-04T03:43:49.370" >
          <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" >
            <identity>
               <name>
                  <displayName>John Doe</displayName>
               </name>
               <email>john.doe@contoso.com</email>
             </identity>
          </contactCard>   </category>
    
       <category name="contactCard" instance="3" publishTime="2010-02-18T05:08:26.060">
          <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard"
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xmlns:xsd="http://www.w3.org/2001/XMLSchema">
             <company>CONTOSO INC</company>
             <title>SENIOR WRITER II</title>
             <office>HOME OFFICE-MOBILE</office>
             <phone type="work">
                <uri>tel:+14255550100;ext=12222</uri>
             </phone>
          </contactCard>
       </category>
       <category name="contactCard" instance="4" publishTime="2010-02-18T05:08:14.427">
         <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" isUCEnabled="true">   </contactCard>
       </category>
    
       <category name="contactCard" instance="6" publishTime="2010-01-10T22:08:16.677">
          <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard">
             <title>SENIOR WRITER II</title>
             <office>HOME OFFICE-MOBILE</office>
             <delimiter xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/contactcard"
                      xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes"></delimiter>
             <delimiter xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/contactcard"
                      xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes"></delimiter>
             <displayADPhoto>false</displayADPhoto>
          </contactCard></category></categories>

All operational attributes do not appear in category instances received in a subscription because the values of certain operational attribute should be confidential. For example, container IDs are excluded from the previous example because containers are the means used by publisher to control who can access a publication.

The following XML example shows a list of state category instances transmitted in a publication. The container ID, version number, and expiry type is specified.

    <publish xmlns="http://schemas.microsoft.com/2006/09/sip/rich-presence">
       <publications uri="sip:mary@contoso.com">
          <publication categoryName="state" instance="945175315" container="2" 
                       version="1" expireType="endpoint">
             <state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
                    manual="false" xsi:type="machineState" 
                    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
               <availability>5000</availability>
               <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
               <timeZoneBias>480</timeZoneBias>
               <timeZoneName>Pacific Standard Time</timeZoneName>
               <timeZoneAbbreviation>Pacific Standard Time</timeZoneAbbreviation>
               <device>computer</device>
               <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes"></end>
             </state>
          </publication>
          <publication categoryName="state" instance="945175315" container="3" 
                       version="1" expireType="endpoint">
             <state manual="false" xsi:type="machineState" 
                    xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
                    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <availability>5000</availability>
                <delimiter xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/state" 
                           xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
                   <timeZoneBias>480</timeZoneBias>
                   <timeZoneName>Pacific Standard Time</timeZoneName>
                   <timeZoneAbbreviation>Pacific Standard Time</timeZoneAbbreviation>
                   <device>computer</device>
                   <end xmlns:auto-ns1="http://schemas.microsoft.com/2006/09/sip/state" 
                        xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes"></end>
             </state>
          </publication>
       </publications>
    </publish>

