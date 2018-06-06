---
title: Parsing media configuration
TOCTitle: Parsing media configuration
ms:assetid: f96e1271-9004-4db7-819a-09614abc0c7c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454675(v=office.15)
ms:contentKeyID: 57093272
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Parsing media configuration


_**Applies to:** Lync 2013 | Lync Server 2013_

In Microsoft Unified Communications Managed API (UCMA), a media configuration is encapsulated by a MediaConfiguration object, which exposes the configuration settings as a collection of name-value pairs known as the properties of the media configuration.

The following code example shows how the media configuration might be parsed by using UCMA.

``` 
        string ParseMediaConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;

            if (data.MediaConfiguration != null && data.MediaConfiguration.Properties != null)
            {
                msg += "\r\nMediaConfiguration:\r\n";
                foreach (string key in data.MediaConfiguration.Properties.Keys)
                {
                    msg += "\tProperty[ " + key + " ] = " + data.MediaConfiguration.Properties[key] + "\r\n";
                }
            }

            return msg;
        }
```

The following example output is generated when the previous code statement is invoked.

    MediaConfiguration:
    Property[ propertyentrylist ] = 
             <property name="bypassEnabled" xmlns="http://schemas.microsoft.com/2006/09/sip/provisiongrouplist-notification">true</property>
             <property name="internalBypassMode" xmlns="http://schemas.microsoft.com/2006/09/sip/provisiongrouplist-notification">Any</property>
             <property name="externalBypassMode" xmlns="http://schemas.microsoft.com/2006/09/sip/provisiongrouplist-notification">Off</property>

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

