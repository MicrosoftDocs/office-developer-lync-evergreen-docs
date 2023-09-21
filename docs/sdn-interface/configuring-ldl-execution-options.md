---
title: Configuring LDL execution options
TOCTitle: Configuring LDL execution options
ms:assetid: 1f21ded1-e0e7-4f62-aa76-7c88b1a224ee
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785208(v=office.15)
ms:contentKeyID: 62952692
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
description: Learn how to configure LDL execution options in Lync 2010/2013 and Lync Server 2010/2013. Step-by-step guide for modifying LDL installation settings.
---

# Configuring LDL execution options

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

You can also modify some options for LDL execution in the LyncDialogListener.exe.config file. Overall, these execution options let the LDL to locate the LSM to retrieve further configuration settings from. The discussion below explains how to select those execution options that cannot be configured via the LSM but must be modified for each LDL installation.

To modify the Lync Dialog Listener (LDL) execution configuration:

1.  Navigate to the LDL installation directory

2.  Open the LyncDialogListener.exe.config file with a text editor

3.  Search for the \<appSettings\> section and make appropriate changes to the relevant entries.

The following example shows an excerpt of the LDL configuration that contains the LDL execution options:

```xml
  <appSettings>
    <add key="submituri" value="http://localhost:9333/LDL" />
    <add key="alternativeuri" value="" />
    <add key="clientcertificateid" value="" />
    <add key="checkdns" value="false" />
  </appSettings>
```

Here, the submituri value specifies the URI to locate the LSM or LSM pool. For HTTP the default port number is 9333 and for HTTPS the default port number is 9332.

> [!NOTE]
> In this release, the URI contains only the REST service portion (i.e., "LDL"), but not any method (e.g, "CallInfo".) This differs from the Lync SDN API 2.0 convention.

The alternativeuri value specifies the URI of a second single LSM, to which LDL will fail over when its connection to the primary LSM is lost. The clientcertificateid contains the thumbprint of an installed client certificate for authentication of this LDL to the LSM if HTTPS is used and mutual authentication is required. 

The checkdns entry is used to override the submituri specification. If it's set to true, the LDL is forced to use the URI defined in the DNS SRV record to locate the LSM. (See [Setting up DNS SRV record](setting-up-dns-srv-record.md))

## See also

- [Configuring Lync SDN Interface 2.1.1 Lync Dialog Listener](configuring-lync-sdn-interface-2-1-1-lync-dialog-listener.md)
- [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

