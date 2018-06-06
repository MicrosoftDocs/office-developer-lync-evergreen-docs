---
title: Registering custom category names
TOCTitle: Registering custom category names
ms:assetid: a4e1b8f2-fda6-409a-b847-ac6ede5a81a9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454641(v=office.15)
ms:contentKeyID: 57093177
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- sql
---

# Registering custom category names


_**Applies to:** Lync 2013 | Lync Server 2013_

To add a new category you must register the category name with Microsoft Lync Server 2013. To register a category name, call the following SQL commands from the command-line OSQL tool that can access the SQL database that is used by Lync Server 2013.

``` sql
  use rtc
  exec RtcRegisterCategoryDef N'aCategoryName'
```

rtc refers to the SQL database name, RtcRegisterCategoryDef is the name of a stored procedure, and aCategoryName is the name of the category to be registered. To run the commands, you must be a Lync Server 2013 administrator.

## See also

#### Concepts

[Programming with Enhanced Presence](programming-with-enhanced-presence.md)

