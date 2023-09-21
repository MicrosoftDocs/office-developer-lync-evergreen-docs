---
title: Serialization of Enhanced Presence category instances
TOCTitle: Serialization of Enhanced Presence category instances
ms:assetid: 718dbc35-cfd4-4575-8fee-9345bf10155d
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454685(v=office.15)
ms:contentKeyID: 57093247
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Serialization of Enhanced Presence category instances

Learn how to create enhanced presence data by using XML Schema Definition (XSD) files.


**Applies to:** Lync 2013 | Lync Server 2013

With XSD files, you can generate presence data according to schema specifications.

To generate the data class from a schema:

1.  Create .NET Framework classes for the XML types defined in the XSD files. You can accomplish this by using Microsoft Xml Schema/DataTypes Support Utility (XSD.exe). This tool is part of the .NET Framework SDK.

2.  Create presence data object by instantiating the resultant classes and assigning appropriate values.

3.  Serialize the presence data object to obtain its XML representation.

4.  Attach the XML blob to the SIP message body. The process used to attach an XML blob to a SIP message depends on the API used by your application.

## In this section

  - [Creating Enhanced Presence data classes from the XML schemas](creating-enhanced-presence-data-classes-from-the-xml-schemas.md)  
    Demonstrates how to use XSD.exe to create C\# classes from a given XSD file.

  - [Instantiating and initializing an Enhanced Presence data class](instantiating-and-initializing-an-enhanced-presence-data-class.md)  
    Demonstrates how to instantiate and initialize an Enhanced Presence data class in C\#.

  - [Serializing an Enhanced Presence data object to an XML element](serializing-an-enhanced-presence-data-object-to-an-xml-element.md)  
    Demonstrates how to serialize an Enhanced Presence data object in C\# to create the corresponding XML string.

## See also

#### Reference

[Lync-defined Enhanced Presence category instance elements](lync-defined-enhanced-presence-category-instance-elements.md)

#### Concepts

[General features of Enhanced Presence](general-features-of-enhanced-presence.md)

[Get started with Enhanced Presence](get-started-with-enhanced-presence.md)

#### Other resources

[Lync Videos on Channel9](http://channel9.msdn.com/tags/lync)

