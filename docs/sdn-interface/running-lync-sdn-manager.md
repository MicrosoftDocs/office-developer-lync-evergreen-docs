---
title: Running Lync SDN Manager
TOCTitle: Running Lync SDN Manager
ms:assetid: 41743ca0-f297-4e11-8bd3-27bab2f4baee
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785214(v=office.15)
ms:contentKeyID: 62952698
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Running Lync SDN Manager

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

This section describes how to run Lync SDN Manager as a Windows service and as a console application.

The LSM Setup Wizards will install, configure, and start Lync SDN Manager service. This service is configured by default with the automatic startup type. However, you can restart it after the configuration is changed or if the service failed.

You can use the Windows Services to determine whether the service is running and, if not, reconfigure and start it. The Windows Services panel also let you change the credentials that are used to run the service.

In general, you run the Lync SDN Manager as a Windows service. In some cases, especially for debugging, you may want to run the LSM as a console application.

## Run LSM as a Windows service

1.  Start Windows Service application.

2.  Search for Lync SDN Manager entry.

3.  If Lync SDN manager is not already started, right-click the entry to select the **Properties** menu item. Click **Start** to restart the service. Click **OK** after the service is restarted.  
    
    ![Lync SDN Manager properties](images/Dn785214.lync_sdn_mgr_properties(Office.15).png "Lync SDN Manager properties")

## Run LSM as console application

Start SDNManager.exe without any parameter and it will start the LSM service in a console application.

