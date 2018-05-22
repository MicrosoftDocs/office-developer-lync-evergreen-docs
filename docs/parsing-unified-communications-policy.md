---
title: Parsing unified communications policy
TOCTitle: Parsing unified communications policy
ms:assetid: 267ee7d8-64b1-471c-afc4-a54fdf970be7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454659(v=office.15)
ms:contentKeyID: 57093268
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Parsing unified communications policy


_**Applies to:** Lync 2013 | Lync Server 2013_

The unified communications (UC) policy specifies how a user’s UC-enabled phone call is handled. This includes whether simultaneous ringing and call-forwarding are allowed and whether the user can transfer or park a call, place a team call, and assign a delegate to answer calls, and email tracing of malicious calls. In the Microsoft Unified Communications Managed API (UCMA), the settings are exposed as a collection of name-value pairs known as the properties of the UC policy configuration.

The following code example shows how a UC policy configuration might be parsed.

``` 
        string ParseUCPolicyConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;

            if (data.UCPolicyConfiguration != null && data.UCPolicyConfiguration.Properties != null)
            {
                msg += "\r\nUCPolicyConfiguration:\r\n";
                foreach (string key in data.UCPolicyConfiguration.Properties.Keys)
                {
                    msg += "\tProperty[ " + key + " ] = " + data.UCPolicyConfiguration.Properties[key] + "\r\n";
                }
            }

            return msg;
        }
```

The following example output is generated when the previous code statements are invoked.

    UCPolicyConfiguration:
    Property[ allowsimultaneousringing ] = true
    Property[ name ] = Users in My Domain
    Property[ enablecalltransfer ] = true
    Property[ enablecallpark ] = true
    Property[ enablebwpolicyoverride ] = false
    Property[ allowcallforwarding ] = true
    Property[ enableteamcall ] = true
    Property[ enabledelegation ] = true
    Property[ enablemaliciouscalltrace ] = false

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

