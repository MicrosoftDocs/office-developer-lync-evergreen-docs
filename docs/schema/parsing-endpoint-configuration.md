---
title: Parsing endpoint configuration
TOCTitle: Parsing endpoint configuration
ms:assetid: 6566b1dd-4c85-41d9-91c1-20848179f30d
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454638(v=office.15)
ms:contentKeyID: 57093346
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Parsing endpoint configuration


**Applies to:** Lync 2013 | Lync Server 2013

In Microsoft Unified Communications Managed API (UCMA), an endpoint configuration specifies the features that are supported on an endpoint. It is exposed by a collection of name-value pairs known as the properties of the endpoint configuration.

The following code example shows how an endpoint configuration might be parsed by using UCMA.

```SCR
     string ParseEndpointConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;
            if (data.EndpointConfiguration != null && data.EndpointConfiguration.Properties != null)
            {
                msg += "\r\nEndpointConfiguration:\r\n";
                foreach (string key in data.EndpointConfiguration.Properties.Keys)
                {
                    string value = data.EndpointConfiguration.Properties[key];
                    msg += "\tProperty[ " + key + " ] = " + value + "\r\n";
                }
            }
            return msg;
        }
```

The following example shows sample output that is derived from the previous code example.

    EndpointConfiguration:
    Property[ searchprefixflags ] = 127
    Property[ showrecentcontacts ] = true
    Property[ showsharepointphotoeditlink ] = false
    Property[ absusage ] = WebSearchOnly
    Property[ p2pappsharingencryption ] = 0
    Property[ showmanageprivacyrelationships ] = false
    Property[ spsearchcenterinternalurl ] = http://contoso/searchcenter/pages/peopleresults.aspx
    Property[ exchangecontactstoreallowed ] = false
    Property[ maximumdgsallowedincontactlist ] = 10
    Property[ enablecontactsync ] = true
    Property[ bitsserveraddressexternal ] = https://comodf.contoso.com/trd/
    Property[ maxphotosizekb ] = 30
    Property[ bitsserveraddressinternal ] = http://oly11-ocg.exchange.contoso.com/trdin
    Property[ photousage ] = AllPhotos
    Property[ showaliasoncontactcard ] = True
    Property[ enablevoipcalldefault ] = false
    Property[ sendfeedbackurl ] = df-mqd-fdb-01
    Property[ enablebackgrounddatacollection ] = 1
    Property[ disablemusiconhold ] = true
    Property[ enableissuereports ] = 1
    Property[ spsearchinternalurl ] = http://contoso/_vti_bin/search.asmx
    Property[ enablebugfiling ] = 1

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

