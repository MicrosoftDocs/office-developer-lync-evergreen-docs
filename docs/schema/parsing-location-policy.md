---
title: Parsing location policy
TOCTitle: Parsing location policy
ms:assetid: 773c5666-2e80-47a7-8889-25fbc02f1f20
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454648(v=office.15)
ms:contentKeyID: 57093267
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Parsing location policy


**Applies to:** Lync 2013 | Lync Server 2013

The location policy from the provisioned data specifies whether emergency services are enabled for the specified location. In Microsoft Unified Communications Managed API (UCMA), the location policy is encapsulated by a LocationPolicyConfiguration object, which exposes the configuration settings as a raw XML string.

The following code example shows how the media configuration might be parsed by using UCMA.

``` 
        string ParseLocationPolicyConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;

            if (data.LocationPolicyConfiguration != null)
            {
                msg += "\r\nLocationPolicyConfiguration:\r\n";
                msg += "\tElementXml = \r\n" + data.LocationPolicyConfiguration.ElementXml + "\r\n";
            }

            return msg;
        }

```

The following example output is generated when the previous code statements are invoked.

```xml
LocationPolicyConfiguration:
ElementXml = 
         <property name="EnhancedEmergencyServicesEnabled" xmlns="http://schemas.microsoft.com/2006/09/sip/provisiongrouplist-notification">false</property>
         <property name="LocationPolicyTagID" xmlns="http://schemas.microsoft.com/2006/09/sip/provisiongrouplist-notification">user-tagid</property>
         <property name="EmergencyServiceDisclaimer" xmlns="http://schemas.microsoft.com/2006/09/sip/provisiongrouplist-notification">This location is used for emergency calls so please enter a location</property>
```

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

