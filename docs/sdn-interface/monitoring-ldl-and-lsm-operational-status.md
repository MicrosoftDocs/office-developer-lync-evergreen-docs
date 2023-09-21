---
title: Monitoring LDL and LSM operational status
TOCTitle: Monitoring LDL and LSM operational status
ms:assetid: 80c3b67f-aa1c-4c06-a175-cdd0208db0a3
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785219(v=office.15)
ms:contentKeyID: 62952703
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Monitoring LDL and LSM operational status

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

In addition to supporting internal logging, LDL and LSM also send events to the Windows EventLog. You can therefore monitor the operational status of the Lync SDN Interface components by examining the EventLog entries sourced from the LDL and LSM in the Windows Event Viewer. For example, the operational status message reports that the LSM or LDL service started or stopped. The error conditions include connection failures to the Lync Server and database or between the LSM and LDL.

The following figure shows an example of the Lync SDN Interface log from the Windows Event Viewer.

**Examining Lync SDN Interface log in Windows Event Viewer**

![Lync SDN Interface log in Windows Event Viewer](images/Dn785219.Lync_sdn_interface_log_in_windows_event_viewer(Office.15).png "Lync SDN Interface log in Windows Event Viewer")

