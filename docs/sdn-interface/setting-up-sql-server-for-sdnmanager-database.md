---
title: Setting up SQL Server for SDNManager database
TOCTitle: Setting up SQL Server for SDNManager database
ms:assetid: 2b38badb-b30d-4003-8d18-c84c150feb91
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785200(v=office.15)
ms:contentKeyID: 62952684
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Setting up SQL Server for SDNManager database


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

In a pool configuration, Lync SDN Interface 2.1.1 uses an SQL database to share call states of concurrently ongoing calls or configuration settings among multiple LSMs. This SDN Manager database is hosted on a SQL server of your choosing. Make sure to select the SQL Server host that supports appropriate behaviors in the presence of fault.

To minimize hardware investments, we recommend that you use the Lync Backend SQL Server, although you can use any SQL Server edition, including the SQL Server Express edition.

The installer creates and configures a new database or joins a new LSM installation with an existing database.

## See also

  - [Getting ready to install Lync SDN Interface 2.1.1](getting-ready-to-install-lync-sdn-interface-2-1-1.md)

  - [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

