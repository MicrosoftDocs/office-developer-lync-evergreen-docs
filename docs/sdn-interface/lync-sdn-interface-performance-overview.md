---
title: Lync SDN Interface performance overview
TOCTitle: Lync SDN Interface performance overview
ms:assetid: 2ba10414-fcc4-40be-b87e-dc52f517c626
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912667(v=office.15)
ms:contentKeyID: 64126837
ms.date: 03/04/2016
mtps_version: v=office.15
---

# Lync SDN Interface performance overview

Provides some guidelines on performance benchmarks for Lync SDN Interface 2.1.1.

**Applies to**: Lync Server 2010 | Skype for Business

This version of Lync SDN Interface 2.1.1 was extensively tested in a production environment and in lab setups but no formal scalability testing has been conducted. The following numbers should give you an idea what you can expect. Please consider these numbers as example only.

## Performance benchmarks

- A pool of two LSM servers can support the traffic from 48 Lync front-ends supporting around 80,000 users in one continent. CPU and memory impact of the LDL in the front-ends is hardly noticeable, while the load in the two LSM reaches overall 50% in high load situations.

- Memory consumption is low and fairly stable.

- Sample machine configuration:
    
   - **Stand-alone LSM server**: Windows Server 2012 R2
    
   - **CPU**: 8 Cores, 8GB of memory
    
   - **Hard drive**: 1 TB

- In lab scenarios, we execute load of 400 audio calls/min against two FEs and two LSMs. These topologies consist of virtual machines only with not more than 2 cores and 8 GB memory assigned each.

- Bandwidth includes the RTCP stream. RTCP streams use a port one number higher than the reported media ports.

- If a pool configuration is used around a database, the SQL Server is expected to be production level server with state-of-the art memory and CPU.

