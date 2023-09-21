---
title: Parsing mobility policy
TOCTitle: Parsing mobility policy
ms:assetid: 1d277266-79d9-4539-aa3e-0a6b54824382
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454645(v=office.15)
ms:contentKeyID: 57093270
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Parsing mobility policy


**Applies to:** Lync 2013 | Lync Server 2013

In Microsoft Unified Communications Managed API (UCMA), mobility policy is encapsulated by the MobilityPolicyConfiguration class. The settings can be obtained by reading the ElementXml property of the object.

``` 
        string ParseMobilityPolicyConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;

            if (data.MobilityPolicyConfiguration != null)
            {
                msg += "\r\nMobilityPolicyConfiguration:\r\n";
                msg += "\tElementXml =\r\n" + data.MobilityPolicyConfiguration.ElementXml + "\r\n";
            }

            return msg;
        }

```

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

