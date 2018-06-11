---
title: Configuring Lync SDN Interface 2.1.1 Lync SDN Manager
TOCTitle: Configuring Lync SDN Interface 2.1.1 Lync SDN Manager
ms:assetid: e66f9787-ab6b-4a77-8895-0ae39a3a5ee1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785209(v=office.15)
ms:contentKeyID: 62952687
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Configuring Lync SDN Interface 2.1.1 Lync SDN Manager

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

Lync SDN Manager (LSM) can run in three different operational modes, depending on how LSM stores and shares states of call streams and configuration settings: Cache, Database, and Split.

- In the Cache mode, the stream state and configuration settings are only kept in a local memory and not shared among the SDN Manager instances. You can only use this option if you run the SDN Manager as a singleton, or in a primary-secondary fail-over configuration.

- In the Database mode, the stream state and configuration settings are stored in a central SQL database. All settings are shared among all LSMs connected to the same database.

- In the Split mode, only configuration settings are stored in a database but the stream state is cached in a local memory.

The LSM operational mode depends on how the Lync SDN Interface is deployed. For more information about the deployment scenarios, see [Deploying Lync SDN Interface 2.1.1](deploying-lync-sdn-interface-2-1-1.md).

In general, the LSM installation determines all the necessary configuration settings, such as those for selecting the deployment mode (mode), connecting to the database (statedbserver, statedbusername, statedbpassword) and specifying the overall logging location. These particular settings cannot be overridden in the database. To change these settings, you must set them directly in the configuration file. After the configuration file is edited, you must restart the LSM service for changes in the configuration file to take effect.

When the LSM database is used to share LSM configuration settings, you must edit only minimal set of settings in the SDNManager.exe.config file. In fact, most settings are overridden by the corresponding values maintained in the database.

You can also configure LSM to maintain logging information for debugging. For information about setting or updating the logging configuration, see [Debugging Lync SDN Manager](debugging-lync-sdn-manager.md)

Depending on how Lync SDN Interface is deployed, you can set or reset the LSM configuration settings by:

- Configuring LSM by editing the SDNManger.exe.config file and then restarting the service.
- Configuring LSM by using the SDNManager.exe command line tool.


> [!NOTE]
> The steps presented in this section are optional unless you want to change the default settings configured during the LSM installation.


## In this section

- [Configuring LSM using the configuration file](configuring-lsm-using-the-configuration-file.md)
- [Configuring LSM using command prompt](configuring-lsm-using-command-prompt.md)
- [Configuring LSM execution options](configuring-lsm-execution-options.md)
- [Configuring LSM to send messages to network controllers](configuring-lsm-to-send-messages-to-network-controllers.md)

## See also

- [Configuring Lync SDN Interface 2.1.1](configuring-lync-sdn-interface-2-1-1.md)
- [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

