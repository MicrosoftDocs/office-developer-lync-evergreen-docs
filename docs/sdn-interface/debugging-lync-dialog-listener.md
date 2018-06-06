---
title: Debugging Lync Dialog Listener
TOCTitle: Debugging Lync Dialog Listener
ms:assetid: 0dade195-3eee-4b8d-8510-33bd78927442
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785218(v=office.15)
ms:contentKeyID: 62952701
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Debugging Lync Dialog Listener


_**Applies to:** Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013_

## Troubleshooting installation of Lync Dialog Listener

LyncDialogListener.exe is a Lync Server application and uses Microsoft SPL (MSPL) to connect to Lync Server. Therefore, it must be registered by using the Lync Server. When an installation of the Lync Dialog Listener fails, it is possible that the LDL is not registered. To troubleshoot, verify that the application is registered by running the Get-CsServerApplication PowerShell cmdlet from the Lync Server Management Shell.

  - Start the Lync Server Management Shell.

  - Issue the following PowerShell cmdlet in the Lync Server Management Shell window:  
    Get-CsServerApplication

  - Verify the following entry (or a similar one) is displayed in the output of the previous cmdlet example:  
      
    ![Verify that the following entry (or a similar one) is displayed in the output of the above cmdlet](images/Dn785218.lync_sdn_api_lync_server_mgmt_shell(Office.15).png "Verify that the following entry (or a similar one) is displayed in the output of the above cmdlet")  
      
    If such an entry is not shown in the output, ensure that you are running in an administrator account that is also member of the *RTC Server Applications* local group before you install LDL.

  - Furthermore you can check whether the current Lync FE is synchronized by using the Get-CsManagementStoreReplicationStatus PowerShell command. This operation may take several minutes and may time out if the synchronization fails.

  - You can use the Get-CsQoEConfiguration PowerShell command to determine whether QoE reporting is activated for this particular Lync Server pool.

  - There is the chance that the LDL service may not start due to incompatible or incorrect credentials. You can verify and update the credentials by starting the LDL service at a command prompt.

An example of the registration script can be found in C:\\ProgramData\\Microsoft\\Lync Dialog Listener\\Register.ps1

## Verifying operations of Lync Dialog Listener service

To confirm that the installation is successful, do the following:

1.  Verify that the LyncDialogListener.exe service has started.

2.  After running the Setup Wizard, you can confirm that the installation is successful by checking the LyncDiagnostics.log file and verifying that there are no errors reported in the log file.

