---
title: Deploying Lync SDN Interface 2.1.1
TOCTitle: Deploying Lync SDN Interface 2.1.1
ms:assetid: 28293ebc-d1f4-4715-b7cd-276055e48015
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785194(v=office.15)
ms:contentKeyID: 62952678
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Deploying Lync SDN Interface 2.1.1

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

Lync SDN Interface 2.1.1 supports different deployment scenarios with noteworthy differences and trade-offs. Regardless of the deployment topology you choose, always install the Lync Dialog Listener (LDL) components on all the Lync Server front ends; these front ends can be Lync Server versions 2010 or later.

## Deploy Lync SDN Interface with a LSM pool

In a Lync SDN Manager (LSM) pool configuration, all LDLs are connected to a DNS load-balanced pool of LSM servers.

In this configuration, the size of the pool scales with the message load produced by the Lync Servers and LDLs. The pool will automatically handle most server failures, but requires a database to maintain a shared and consistent state among all the LSMs in the pool. Network Controllers connected to this LSM pool will receive a consistent state about applicable media streams handled by the connected Lync Server Front-End pools. The setup provides the option for a disaster pool failover configuration. If all LSMs in a pool are unreachable, LDLs may be configured to fail-over to use an alternative pool.

**Figure 1. Deployment of Lync SDN Interface with a pool of LSMs**
 
![Deploying Lync SDNI with LSM pool](images/Dn785194.Lync_sdn_interface_deploy_with_LSM_pool(Office.15).png "Deploying Lync SDNI with LSM pool")

## Deploy Lync SDN Interface with a single LSM

In this simple configuration, all LDLs are connected to a single LSM component. The LSM service maintains its call state information in memory and a database is not required. This configuration is useful when the call load is under the limit that a single LSM can support and fault-tolerance is not required.

## Deploy Lync SDN Interface with primary/secondary failover

To overcome server failures and simplify upgrade, the Lync SDN interface can take a second LSM as a failover alternate for all the connected LDLs. When a disconnected LDL attempts to deliver messages to the primary LSM, a failover protection algorithm will switch to the alternative LSM to ensure that the Lync SDN Interface provides continuous service when server failures occur. 

In this case, the alternate LSM becomes the new primary service provider. Call states are lost during the failover transition, because state is kept in memory. This is likely to cause somewhat inconsistent or incomplete message reporting delivered to the network controllers until the new active LSM can establish a consistent view of the ongoing media streams.

> [!NOTE]
> In the event of failover, the secondary computer will continue to be used even if the primary comes back on line. In that scenario, the primary is used again only if the secondary goes offline.

**Figure 2. Deployment of Lync SDN Interface with primary and secondary LSMs**

![Deploying Lync SDNI with primary and secondary LSM](images/Dn785194.Lync_sdn_interface_deploy_with_primary_secondary_LSMs(Office.15).png "Deploying Lync SDNI with primary and secondary LSM")

## Deploy Lync SDN Interface with LSM collocated with LDL

In this configuration, the LSM component is installed on the Front-End. Call states are usually maintained in memory and they are not shared with other LSMs. The collocated LSM can only report the local streams and events of the hosting Lync Server, if the clients stay connected to the same Front-End during a call. Often, two different Lync Front-Ends are involved in handling a call, with each receiving possibly different (quality) data. 

A network controller connected to both LSMs will get duplicate messages and might need to merge quality information itself to get a more complete picture. Adding a LSM to the Lync Server will increase the load (CPU, memory, and possibly network) on these servers. When the LDL and the LSM are installed on several Lync Front-Ends, the Lync SDN Interface 2.1.1 supports sharing the settings for all these components in a database. In this case, the interface is then in what is called the Split mode. The load or survivability requirement on this database is minimal because only the settings are stored there while ongoing call state is still maintained in memory.

**Figure 3. Deployment of Lync SDN Interface with LSM collocated with LDL**

![Deploying Lync SDNI with LSM collocated with LDL](images/Dn785194.Lync_sdn_interface_deploy_with_lsm_colloated_with_ldl(Office.15).png "Deploying Lync SDNI with LSM collocated with LDL")

## See also

- [Understanding Lync SDN Interface 2.1.1](understanding-lync-sdn-interface-2-1-1.md)
- [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

