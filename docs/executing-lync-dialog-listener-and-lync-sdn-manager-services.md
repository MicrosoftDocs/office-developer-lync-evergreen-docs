---
title: Executing Lync Dialog Listener and Lync SDN Manager services
TOCTitle: Executing Lync Dialog Listener and Lync SDN Manager services
ms:assetid: 5cb9889e-0b19-4d82-aa5d-b6ee8721f355
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439304(v=office.15)
ms:contentKeyID: 57261040
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Executing Lync Dialog Listener and Lync SDN Manager services


_**Applies to:** Lync 2013 | Lync Server 2013_

This section describes how to execute the Lync Dialog Listener and Lync SDN Manager services.

## Executing the Lync Dialog Listener service

The Lync SDN API 2.0 Setup Wizards will install, configure, and start the Lync Dialog Listener and Lync SDN Manager services. These services are configured by default with the automatic startup type. However, you can restart it by after the configuration is changed or the service failed.

You can use the Windows Services to verify if the services are indeed automatically started and, if not, reconfigure them to be started automatically. The Windows Services panel also let you change the credentials used to run the service, access the Lync server (if you are in the RTC Server Administrator group) as well optionally access the QoE database when using a Windows-trusted database connection..

### Managing the Lync Dialog Listener service

1.  Start the Windows Service application.

2.  Search for the "Lync Dialog Listener" entry.  
      
    ![Search dialog box for the Lync Dialog Listener entry](images/Dn785217.lync_sdn_api_search_ldl(Office.15).png "Search dialog box for the Lync Dialog Listener entry")  

3.  If Lync Dialog Listener is not already started, right-click the entry to select the **Properties** menu item. Click **Start** to restart the service. Click **OK** after the service is restarted.  
      
    ![Lync Dialog Listener Properties sheet](images/Dn439304.lync_sdn_api_ldl_properties(Office.15).png "Lync Dialog Listener Properties sheet")  

### Managing Lync SDN Manager service

1.  Start Windows Service application.

2.  Search for Lync SDN Manager entry.

3.  If Lync SDN manager is not already started, right click the entry to select Properties menu item. Click Start to restart the service. Click OK after the service is restarted.  
    
    ![Lync SDN Manager properties](images/Dn785214.lync_sdn_mgr_properties(Office.15).png "Lync SDN Manager properties")

### Verifying operations of Lync Dialog Listener service

To confirm that the installation is successful, do the following:

1.  Verify that the LyncDialogListener.exe service has started.

2.  After running the Lync SDN API 2.0 Setup Wizard, you can confirm that the installation is successful by checking the LyncDiagnostics.log file and verifying that an entry analogous to the following line is logged in the log file.  
      
    2013-04-18T14:17:31.7693761-07:00\[Info\]Lync DialogListener Diagnostics Service started.

3.  The log file is located in the directory specified during the setup. By default, this is the %temp%\\SDN directory. You can change this value to a custom directory path by using the Lync SDN API 2.0 Setup wizard during the installation or by editing the LyncDialogListener.exe.config file after the installation.

