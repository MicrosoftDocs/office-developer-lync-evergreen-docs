---
title: Serializing an Enhanced Presence data object to an XML element
TOCTitle: Serializing an Enhanced Presence data object to an XML element
ms:assetid: 081c36e2-a225-43ca-9c8c-09f54308314f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454689(v=office.15)
ms:contentKeyID: 57093337
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Serializing an Enhanced Presence data object to an XML element


**Applies to:** Lync 2013 | Lync Server 2013

The following example serializes a .NET Framework class into an XML string.

```csharp
using System;
using System.Xml;
using System.Xml.Serialization;
using System.IO;
using System.Globalization;

/// <summary>
/// This method wraps an XmlSerializer and turns a presence data class 
/// object into its corresponding XML string
/// </summary>
/// <param name="objectToSerialize">
/// A presence data class object to be serialized into the string
/// representation of an XML element according to the definition of
/// the type specified in the second parameter of this method. 
/// </param>
/// <param name="type">The type of object to serialize. Depending 
/// on the XML Schema definition, this may have to be a super type 
/// of the object specified in the first parameter</param>
/// <returns>An XML string of the specified presence data</returns>
public static String Serialize(Object objectToSerialize, Type type)
{
     if (objectToSerialize == null) 
        throw new ArgumentNullException("objectToSerialize");
     if (type == null) 
        throw new ArgumentNullException("type");

     XmlSerializer serializer = new XmlSerializer(type);
     StringWriter sw = new StringWriter(new StringBuilder(128), 
                                 CultureInfo.InvariantCulture);
     XmlWriterSettings setting = new XmlWriterSettings();
     setting.OmitXmlDeclaration = true;
     setting.Indent = true;
     setting.IndentChars = "   ";
     setting.NewLineOnAttributes = true;
     XmlWriter messageWriter = XmlWriter.Create(sw, setting);
     serializer.Serialize(messageWriter, objectToSerialize);
     messageWriter.Close();
     sw.Close();

     return sw.ToString();
}
```

## See also

#### Concepts

[Creating Enhanced Presence data classes from the XML schemas](creating-enhanced-presence-data-classes-from-the-xml-schemas.md)

[Instantiating and initializing an Enhanced Presence data class](instantiating-and-initializing-an-enhanced-presence-data-class.md)

[Serialization of Enhanced Presence category instances](serialization-of-enhanced-presence-category-instances.md)

