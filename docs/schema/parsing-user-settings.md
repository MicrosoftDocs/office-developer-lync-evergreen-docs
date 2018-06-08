---
title: Parsing user settings
TOCTitle: Parsing user settings
ms:assetid: 195879fa-f58b-4f74-be85-a5e48b9a5738
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454652(v=office.15)
ms:contentKeyID: 57093273
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Parsing user settings


**Applies to:** Lync 2013 | Lync Server 2013

The user setting from the provisioned data specifies the location profile assigned to the user as well as the permission to perform file transfer. In Microsoft Unified Communications Managed API (UCMA), a user setting is encapsulated by a UserSettingConfiguration object, which exposes the configuration settings as a collection of name-value pairs known as the properties of the media configuration.

The following code example shows how the user setting might be parsed by using UCMA.

``` 
        string ParseUserSettingConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;

            if (data.UserSettingConfiguration != null)
            {
                msg += "\r\nUserSettingConfiguration:\r\n";
                msg += "\tUserLocationProfile = " + data.UserSettingConfiguration.UserLocationProfile + "\r\n";

                if (data.UserSettingConfiguration.Properties != null)
                    foreach (string key in data.UserSettingConfiguration.Properties.Keys)
                    {
                        msg += "\tProperty[ " + key + " ] = " + data.UserSettingConfiguration.Properties[key] + "\r\n";

                    }
            }
            return msg;
        }
```

The following example output is generated when the previous code statements are invoked.

    UserSettingConfiguration:
    UserLocationProfile = W13RC1
    Property[ ucuserlocationprofile ] = W13RC1
    Property[ disablefiletransfer ] = false

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

