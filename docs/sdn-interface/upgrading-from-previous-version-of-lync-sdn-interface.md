---
title: Upgrading from previous version of Lync SDN Interface
TOCTitle: Upgrading from previous version of Lync SDN Interface
ms:assetid: 8d3c28fa-dabe-4a52-9882-a6663ced5217
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912664(v=office.15)
ms:contentKeyID: 64126835
ms.date: 03/04/2016
mtps_version: v=office.15
---

# Upgrading from previous version of Lync SDN Interface


**Applies to**: Lync Server 2010 | Skype for Business

Currently, neither LDL nor LSM supports multiple parallel installations. Please expect downtime of the Lync SDN Interface service during the upgrade, although in some cases it can be minimized. However, there is no downtime for the Lync service required for upgrading Lync SDN Interface. Regardless, please perform upgrades only during off-hours and with minimal load on all components. Generally, it is recommended that you perform the upgrade in multiple steps. The following process assumes you want the service to remain active as long as possible.

## Upgrade from version 2.1 to 2.1.1

Lync DialogListener 2.1 clients are compatible with LyncSDNManager 2.1.1. The database structure is basically compatible, although older version 2.1 LSM nodes may have issues interpreting some changes in the content once version 2.1.1 LSMs have written to it.

1.  Remove one LSM after another from the pool. Observe in the log or PerfMon that no calls are any longer forwarded to the LSM before shutting it down, uninstalling 2.1 and re-installing 2.1.1. In primary/secondary configuration, upgrade the currently inactive LSM server first. In co-located scenarios simply uninstall and re-install one LSM.

2.  Before upgrading the last LSM in a pool, you should switch the pool configuration to now actively use the already upgraded pool servers and remove the last LSM from the pool. In primary/secondary configuration you would force a fail-over by shutting down the current primary to the upgraded server before upgrading this previous primary.

3.  The final LSM should now be upgraded and joined to the pool.

4.  After upgrading the LSMs, LDL can upgraded at a leisure and pool per pool.

5.  Uninstall the LDL 2.1 component.

6.  Install the LDL 2.1.1 component. Executing the registration script is not needed and therefore using the msiexec’s commandline option SKIPREGISTRATION=1 is recommended. In this case, the service needs to be started manually. (See more details in [Unattended installation of LSM](unattended-installation-of-lsm-and-ldl.md).)

## Upgrade from version 2.0 to 2.1.1

Neither the LDL nor the LSM components are compatible between 2.0 and 2.1.1. Consider using the newer LSM pool configuration in 2.1.1

1.  As you cannot have both LSMs versions installed and running on the same server, you will need to install a separate LSM server with 2.1.1. In a co-located configuration simply shutdown the LDL service, upgrade each LSM and LDL in that order, one Lync Server at the time.

2.  After at least the first LSM is operational, you should upgrade one LDL after the other pointing to the new LSM (pool).

Clearly, data may be inconsistently reporting during the upgrade process

