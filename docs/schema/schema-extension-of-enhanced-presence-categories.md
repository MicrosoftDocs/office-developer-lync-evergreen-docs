---
title: Schema extension of Enhanced Presence categories
TOCTitle: Schema extension of Enhanced Presence categories
ms:assetid: e90758c9-d35d-4a2e-b163-ece25bac71b3
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454679(v=office.15)
ms:contentKeyID: 57093217
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Schema extension of Enhanced Presence categories


**Applies to:** Lync 2013 | Lync Server 2013

Schema extensions for existing enhanced presence categories are made by the schema designer. Using such extensions, the schema designer can update a given category schema from one version to the next.

Schema extensions add additional child elements to existing category. The added elements are in the same namespace of the given category. This type of extension is enclosed by a [delimiter element](delimiter-element.md) element and an [end element](end-element.md) element. Multiple delimiter elements can occur and each of the elements marks the beginning of an extension introduced in a particular version.

As an example, the following shows a [state\[@type='machineState'\] element](state-element_2.md) category instance containing a schema extension that was introduced in Microsoft Office Communications Server 2007 R2.

```xml
<state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       manual="false" 
       xsi:type="machineState">
   <availability>3500</availability>
   <endpointLocation>31/West Wing Redmond</endpointLocation>
   <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
   <timeZoneBias>480</timeZoneBias>
   <timeZoneName>Pacific Standard Time</timeZoneName>
   <timeZoneAbbreviation>Pacific Standard Time</timeZoneAbbreviation>
   <device>computer</device>
   <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
</state>
```

In the previous example, the schema extension adds [state/timeZoneBias element](state-timezonebias-element.md), [state/timeZoneName element](state-timezonename-element.md), [state/timeZoneAbbreviation element](state-timezoneabbreviation-element.md), and [state/device element](state-device-element.md) elements. The added elements are from the same namespace as the parent element. The extension is not rendered by Lync prior to Microsoft Office Communicator 2007 R2.

## See also

#### Concepts

[Extension and customization of a category schema](extension-and-customization-of-a-category-schema.md)

