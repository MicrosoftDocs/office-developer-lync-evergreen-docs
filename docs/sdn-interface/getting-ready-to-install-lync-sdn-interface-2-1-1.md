---
title: Getting ready to install Lync SDN Interface 2.1.1
TOCTitle: Getting ready to install Lync SDN Interface 2.1.1
ms:assetid: c5b5083a-a25e-4409-a496-2616bb2b15a2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785199(v=office.15)
ms:contentKeyID: 62952683
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Getting ready to install Lync SDN Interface 2.1.1


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

To ensure that the Lync SDN Interface 2.1.1 components are successfully installed and started, do the following before you run the installation packages:

1.  Set up any required DNS records to define a round-robin fqdn pool or SRV records.

2.  Close Service Control Panel to prevent the Windows service installation from hanging.

3.  Ensure that the Lync Front-End Servers and LSM servers have reasonably synchronized clocks. This is especially true for the LSMs process timeouts, which rely on timestamps. Note, too, that significantly divergent times will cause unexpected behavior as well as the uneven distribution of loads.

4.  If you choose, install all certificates necessary for mutual TLS. Create and place the same client certificate on every LDL, and obtain client certificates expected and authorized by each the network controller on all LSMs.

5.  Install LDL. Run the LyncDialogListener.msi installer on a Lync Server Front-End role from an administrator account that is also a part of the *RTC Server Applications* local group. To add the administrator account to the *RTC Server Applications* group, follow these steps:
    
    1.  Log on to the Lync Server Front-End server computer as the administrator and start the server manager snap-in.
    
    2.  Add the administrator account to the *RTC Server Applications* local group.
    
    When you run Steps 5a and 5b, log off and log on again for the changes to take effect. The LDL service account must be a member of the RTC Local Server Group.


> [!NOTE]
> <P>You should install LSM, (run the LyncSDNManager.msi installer) on a separate application server to maximize the performance of the Lync Server Front End.</P>



## In this section

  - [Setting up DNS SRV record](setting-up-dns-srv-record.md)

  - [Setting up SQL Server for SDNManager database](setting-up-sql-server-for-sdnmanager-database.md)

  - [Installing certificates for the LDL, LSM and network controller](installing-certificates-for-the-ldl-lsm-and-network-controller.md)

  - [Activating QoE recording](activating-qoe-recording.md)

## See also

  - [Installing Lync SDN Interface 2.1.1](installing-lync-sdn-interface-2-1-1.md)

  - [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

