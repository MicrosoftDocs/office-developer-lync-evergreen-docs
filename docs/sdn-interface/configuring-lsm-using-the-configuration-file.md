---
title: Configuring LSM using the configuration file
TOCTitle: Configuring LSM using the configuration file
ms:assetid: 91a71769-df75-49a6-b305-8d202f6a5d12
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785210(v=office.15)
ms:contentKeyID: 62952693
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Configuring LSM using the configuration file


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

You can edit the SDNManager.exe.config file to configure LSM. The SDNManager.exe.config file is located in the default installation directory, where you will also find SDNManager.exe.

The following example shows an example from the \<appSettings\> section in the configuration file that contains the necessary configuration settings:

```xml
<add key="mode" value="Database" />
<add key="statedbserver" value="localhost" />
<add key="statedbusername" value="" />
<add key="statedbpassword" value="" />
```

Here, the Mode entry describes the operational mode of the LSM. All LSM in a LSM pool must have the same setting. Valid settings are Cache, Database, or Split. The StateDbServer, StateDbUserName, and StateDbPassword entries describe the connection to the shared LSM database. If no user name is specified, integrated security is used. The statedbserver value can be an SQL Server name (e.g., localhost) or an SQL Server instance name (e.g., localhost/LsmDb).


> [!NOTE]
> <UL>
> <LI>
> <P>If settings are shared using the SDNManager database, modifying any other settings than shown previously in this topic in the configuration file directly has no effect. You must use the SDNManager.exe command line tool to change settings in the database.</P>
> <LI>
> <P>If settings are only kept in-memory, trying to change these settings using the command line tool will result in changing these settings in-memory, because the configuration file is read-only to the service. Any changes will be lost when the service restarts. To make the changes persistent in this case, you must edit all the parameters in the configuration file manually or reapply the saved settings using the SDNManager command line tool after the LSM service is restarted.</P>
> <LI>
> <P>Changes to the config file will take effect only after restarting.</P></LI></UL>


