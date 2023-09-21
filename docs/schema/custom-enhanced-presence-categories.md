---
title: Custom Enhanced Presence categories
TOCTitle: Custom Enhanced Presence categories
ms:assetid: 4864d4a2-0a82-4198-ba85-579d8e3a8acf
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454684(v=office.15)
ms:contentKeyID: 57093244
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Custom Enhanced Presence categories


**Applies to:** Lync 2013 | Lync Server 2013

Custom enhanced presence categories can be used to support application-specific presence features not yet supported by any existing enhanced presence schemas. For example, you want to expose the GPS coordinates with an address to indicate the device location of a user. You can define a custom category element to specify this location data as follows.

```xml
<GPSLocation latitude="47.640071" longitude="122.129598">
   <address>1 Microsoft Way, Redmond, WA 98052-6399, USA</address>
</GPSLocation>
```

Before you can publish this GPS location data as a category instance, you must register the category name, namely GPSLocation, with Microsoft Lync Server 2013. For information about registering a custom category name with the server, see [Registering custom category names](registering-custom-category-names.md).

For other applications to parse and render any custom category instances, you must document the custom category instance elements and share the information with other application developers. Otherwise, the custom presence data is ignored by other applications.

## See also

#### Concepts

[Extension and customization of a category schema](extension-and-customization-of-a-category-schema.md)

