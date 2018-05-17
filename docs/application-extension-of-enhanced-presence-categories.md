---
title: Application extension of Enhanced Presence categories
TOCTitle: Application extension of Enhanced Presence categories
ms:assetid: c421e268-877d-4ebe-a31e-d52dd3c38f6c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454683(v=office.15)
ms:contentKeyID: 57093238
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Application extension of Enhanced Presence categories


_**Applies to:** Lync 2013 | Lync Server 2013_

Application extensions of enhanced presence categories are made by the application developer who uses an enhanced presence category schema designed by others. They are used support application-specific extensions to an existing enhanced presence category.

The application extension is contained in the optional [extension element](extension-element.md) element. An application can choose to add any elements of any namespace to this extension element.

For example, an application might want to extend the [state\[@type='userState'\] element](state-element.md) category instance value element by adding some GPS location information. It can do so by specifying the added information in an **extension** element.

    <state xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
           xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
           xsi:type="userState">
       <availability>9500</availability>
        <activity token="in-a-meeting">
           <custom LCID="1033">Some activity</custom>
        </activity>
        <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes">
            <xt:GPSLocation xmlns:xt="some-ns" latitude="47.640071" longitude="122.129598">
               <xt:address>1 Microsoft Way, Redmond, WA 98052-6399, USA</xt:address>
            </xt:GPSLocation>
        </ct:extension>
    </state>

Unless the extension is handled by other applications, the application extension of an existing enhanced category instance is ignored by the other applications.

## See also

#### Concepts

[Extension and customization of a category schema](extension-and-customization-of-a-category-schema.md)

