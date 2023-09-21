---
title: Running Lync Dialog Listener
TOCTitle: Running Lync Dialog Listener
ms:assetid: f405de17-b1be-419e-a301-4055a4dfdaad
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785217(v=office.15)
ms:contentKeyID: 62952702
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Running Lync Dialog Listener


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

This section describes how to execute the Lync Dialog Listener as a Windows service and as a console application.

The LDL Setup Wizards will install, configure, and start the Lync Dialog Listener as a Windows service. With the default configuration, the service is set to start automatically. You can restart it after the configuration is changed or when the service fails. You can use the Windows Services panel to verify the service and reconfigure it. The Windows Services panel lets you change the credentials that you use to run the service. These credentials are used to access the Lync Server, as long as the service is run from an account that is in the *RTC Server Applications* group and granted the logon as service rights in the local Group Policy.

In general, the Lync Dialog Listener executes as Windows Service. In some case, particularly for debugging and for replay, you can run LDL as a console application at the command prompt.

> [!NOTE]
> Unlike the LSM, you're not able to run the service and the command line tool at the same time.

## Run LDL as a Windows service

1.  Start the Windows Service application.

2.  Search for the "Lync Dialog Listener" entry.  
      
    ![Search dialog box for the Lync Dialog Listener entry](images/Dn785217.lync_sdn_api_search_ldl(Office.15).png "Search dialog box for the Lync Dialog Listener entry")  

3.  If Lync Dialog Listener is not already started, right-click the entry to select the **Properties** menu item. Click **Start** to restart the service. Click **OK** after the service is restarted.  
      
    ![Lync Dialog Listener Properties sheet](images/Dn785217.lync_sdn_api_ldl_properties(Office.15).png "Lync Dialog Listener Properties sheet")  
    
    If the service does not start, you may need different user credentials. The user must also be in the local *RTC Server Applications* security group. You can change the user credentials to run the service by using the Lync Dialog Listener Properties panel shown previously.

## Run LDL as a console application

Start LyncDialogListener.exe without any parameter and it will start the service as a console application. Running LDL as a console application, you get more feedback from the LDL service, in particular around issues related to start-up and connecting to the Lync Server. It will also help identifying or confirming issues around credential used to run LDL having the appropriate access rights.

