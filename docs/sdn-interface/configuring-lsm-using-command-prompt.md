---
title: Configuring LSM using command prompt
TOCTitle: Configuring LSM using command prompt
ms:assetid: 3720e38a-b444-4a90-9a1b-cad39292ffdf
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785211(v=office.15)
ms:contentKeyID: 62952691
ms.date: 02/16/2015
mtps_version: v=office.15
description: Learn how to configure LSM using command prompt for Lync SDN Interface. Get and set limits, replay sequences, and modify settings with ease.
---

# Configuring LSM using command prompt

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

As a new feature introduced in Lync SDN Interface 2.1.1 (and 2.1), you can now use the command-line tool (SDNManager.exe) to get and set limits as quality metrics of call streams in the Lync QoEMetrics database. You can also replay sequences of logged messages for testing.

> [!NOTE]
> The command line tool can be used while the service is running. The service will pick up parameter changes as well as report the current parameter settings for the service.

The executable is located in the LSM installation directory. By default, it's **C:\\Microsoft Lync Server\\Lync SDN Manager**.

## Command-line commands

To get or set an LSM configuration setting, run SDNManager.exe to start the appropriate command-line commands.

To get help on available commands, do the following at the command prompt:

`C > SDNManager.exe /?`

This produces the following output:

```
    Lync SDN Manager  2.1, Build Version: 6.0.XXXX.X, Schema Version: C
    Copyright (C) Microsoft Corporation.  All rights reserved.
    
        /?        Help
    
        /u [culture] filename [http(s)://site/LDL] [thumbprint]
                 ....   Upload & store culture-aware (e.g., en-US or current machine culture)
                        configuration into the datastore
                        through the SDN Manager service referred to by the url or the local service
                        using the client certificate thumbprint.
    
        /d [culture] [filename] [http(s)://site] [thumbprint]
                 ....   Download culture-aware (e.g., en-US or current machine culture)
                        configuration from the store into a local file from the
                        SDN Manager service (referred to by the url or the local service)
                        using the client certificate thumbprint.
    
        /p [culture] name=value [http(s)://site] [thumbprint]
                 ....   Set an individual culture-aware (e.g., en-US or current machine culture)
                        configuration value in the SDN Manager service (referred to by the url
                        or the local service) using the client certificate thumbprint.
    
        /e filename  [http(s)://site] [thumbprint]
                 ....   Send content of the file as messages to the
                        SDN Manager service (referred to by the url or the local service)
                        using the client certificate thumbprint
                        and process these messages.
    
        /et filename  [http(s)://site] [thumbprint]
                 ....   Send content of file as messages to the
                        SDN Manager service (referred to by the url or the local service)
                        using the client certificate thumbprint
                        and process these messages with the given timing preserved.
    
        /q dbserver [user] [password] [http(s)://site] [thumbprint]
                 ....   Retrieve threshold values from a QoE database with the specified user
                        name and password and store them in the SDN Manager service
                        (referred to by the url or the local service)
                        using the client certificate thumbprint.
    
              […] designates an optional parameter.
```

## Examples

The following is an example of getting the configuration settings using SDNManager.exe.

```
c:>SDNManager.exe /d
    Response code: SUCCESS Detail: Logical Version 1
```

An example of the corresponding output will look like this:

```xml
    <Configuration Version="1.0">
      <parameter key="submituri">http://localhost:9333/Log/putstuffhere</parameter>
      <parameter key="mode">Cache</parameter>
      <parameter key="hidepii">true</parameter>
      …
    </Configuration>
```

For a complete example of the output, see [Appendix to Lync SDN Interface 2.1.1](appendix-to-lync-sdn-interface-2-1-1.md).

## Modify settings

To modify a setting, use the /p command, specifying a configuration option as the input parameter. The following example shows how to modify the hidepii option to disable SIP obfuscation for a specified LDL service:

`C:\>SDNManager.exe /p hidepii=false https://sdnhost.contoso.com/LDL 23991123649b4cfcb48ccf14f2d08601221caa2c`

In this example, the change prevents obfuscating personally identifiable information (PII) in an LSM service (as identified by https://sdnhost.contoso.com/LDL) with a client certificate thumbprint (23991123649b4cfcb48ccf14f2d08601221caa2c) for authentication.

In addition, you can also get all the threshold settings from the Lync Server QoEMetrics database. The LSM will use the downloaded thresholds to update the corresponding settings in memory or in the SDNManager database. This is shown in the following example:

`C:\>SDNManager.exe /q myLyncBackEnd\monitoring`

Here, myLyncBackEnd\\monitoring is the SQL Server hosting the Lync Server QoEMetrics database. The threshold limits used for determining the stream quality will be updated.

