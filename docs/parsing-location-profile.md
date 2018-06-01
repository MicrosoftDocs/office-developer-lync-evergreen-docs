---
title: Parsing location profile
TOCTitle: Parsing location profile
ms:assetid: f684c168-0770-4e43-8eab-f0e71f4cf6a2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454637(v=office.15)
ms:contentKeyID: 57093102
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Parsing location profile


_**Applies to:** Lync 2013 | Lync Server 2013_

A location profile from the provisioned data specifies the rules that are used to support abbreviated dialing sequences for local or internal calls within a given location. In Microsoft Unified Communications Managed API (UCMA), a location profile is encapsulated by a LocationProfileConfiguration object, which exposes the profile as a set of normalization rules in addition to the ExternalAccessPrefix and OptimizedDevieDialing flags.

The following code example shows how a location profile might be parsed by using UCMA.

```SCR  
        string ParseLocationProfileConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;

            if (data.LocationProfileConfiguration != null)
            {
                msg += "\r\nLocationProfileConfiguration:\r\n";
                msg += "\tName = " + data.LocationProfileConfiguration.Name + "\r\n";
                msg += "\tNormalizationRules : \r\n";
                foreach (NormalizationRule rule in data.LocationProfileConfiguration.NormalizationRules)
                {
                    msg += "\t\tRule pattern = " + rule.Pattern + ", translation = " + rule.Translation + "\r\n";
                }
                msg += "\tExternalAccessPrefix = " + data.LocationProfileConfiguration.ExternalAccessPrefix + "\r\n";
                msg += "\tOptimizeDeviceDialing = " + data.LocationProfileConfiguration.OptimizeDeviceDialing + "\r\n";
            }

            return msg;
        }

```

The following example output is generated when the previous code statements are invoked.

    LocationProfileConfiguration:
    Name = Area 999
    NormalizationRules : 
    Rule pattern = ^1([0-9]{4})$, translation = +1999421$1
    Rule pattern = ^2([0-9]{4})$, translation = +1999722$1
    Rule pattern = ^3([0-9]{4})$, translation = +1999703$1
    Rule pattern = ^4([0-9]{4})$, translation = +1999704$1
    Rule pattern = ^5([0-9]{4})$, translation = +1999705$1
    Rule pattern = ^6([0-9]{4})$, translation = +1999706$1
    Rule pattern = ^7([0-9]{4})$, translation = +1999707$1
    Rule pattern = ^8([0-9]{4})$, translation = +1999538$1
    Rule pattern = ^0$, translation = +19997075555
    Rule pattern = ^911$, translation = +911
    Rule pattern = ^([4,5,7]11)$, translation = +$1
    Rule pattern = ^(\d{7})$, translation = +1999$1
    Rule pattern = ^([2-9]\d{9})$, translation = +1$1
    Rule pattern = ^([2-9]\d\d[2-9]\d{6})$, translation = +1$1
    Rule pattern = ^(1[2-9]\d{9})$, translation = +$1
    Rule pattern = ^011(\d*)$, translation = +$1
    Rule pattern = ^(\+?)(\d+)(X|x|EXT)(\d+)$, translation = $1$2;ext=$4
    Rule pattern = ^(119)$, translation = $1
    ExternalAccessPrefix = 9
    OptimizeDeviceDialing = True

This location profile specifies abbreviated dialing sequences for local or internal calls within a fictitious 999 area code.

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

