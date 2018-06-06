---
title: Modifying an existing publication
TOCTitle: Modifying an existing publication
ms:assetid: 707bce3e-97eb-4ca3-862d-de99ffa25e94
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454642(v=office.15)
ms:contentKeyID: 57092887
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Modifying an existing publication


_**Applies to:** Lync 2013 | Lync Server 2013_

In Microsoft Lync Server 2013, modifying an existing publication means republishing the category instances of the same name, instance ID and container ID, but with different expiry policies, plus any required expiration time, or XML data values. Each modification is equivalent to a new publication with a higher version number. UCMA automatically increments the version number by one.

The following example updates an already published personal note presence category instance in the custom Container 1000 with a new message.

``` csharp
string presenceNoteValue = 
         "<note xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\"" + 
         "      xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\"" + 
         "      xmlns=\"http://schemas.microsoft.com/2006/09/sip/note\">" + 
         "  <body type=\"personal\" uri=\"\">New Personal Note Message</body>" + 
         "</note>";

PresenceCategoryWithMetaData pcm = CreatePresenceCategoryInstance(
                    "note", 0, 1000, presenceNoteValue);

RequestGrammarFreePresencePublication(
                     new PresenceCategoryWithMetaData[]{pcm}); 
```

To change the expiration type (and the expiration time, if necessary) of this note category instance from endpoint-bound to static-bound, reset the **ExpiryPolicy** property and republish the modified category instance in a separate publication request.

``` csharp
pcm.ExpiryPolicy = PresenceCategoryWithMetaData.User;

RequestGrammarFreePresencePublication(
                     new PresenceCategoryWithMetaData[]{pcm}); 
```

## See also

#### Concepts

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

