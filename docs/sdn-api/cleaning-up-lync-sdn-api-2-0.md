---
title: Cleaning up Lync SDN API 2.0
TOCTitle: Cleaning up Lync SDN API 2.0
ms:assetid: cde7eda9-d231-41b6-88bc-bd2fad2bd4d5
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439305(v=office.15)
ms:contentKeyID: 57261041
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Cleaning up Lync SDN API 2.0

**Applies to:** Lync 2013 | Lync Server 2013

This section describes how to clean up the Lync SDN API 2.0 and Lync SDN Manager services.

Cleaning up the Lync SDN API 2.0 involves removing the registration of LDL as a Lync Server application, and uninstalling the Lync Dialog Listener and Lync SDN Manager services.

## Unregister Lync Dialog Listener as Lync server application

To unregister Lync Dialog Listener as a Lync Server application, run the Remove-CsServerApplication cmdlet following these steps:

1.  Start a Lync Server Management Shell window and then issue the following cmdlet:

2.  Issue the following cmdlet:  
      
    ```powershell
    Remove-CsServerApplication -Identity <app identity>  
    ```
      
    Where \<app identity\> is the application identity string; for example, "Service:registrar:pool1.contoso.com/Diagnostics". You can follow the example shown in [Installing Lync SDN API 2.0 components](installing-lync-sdn-api-2-0-components.md) to use Get-CsServerApplication cmdlet to find out the \<app identity\> of the application.

## Uninstall the Lync Dialog Listener (LDL)

To uninstall the LDL, follow these steps:

1.  On the LDL server, launch Control Panel to open Program and Features.

2.  Select Lync SDN API 2.0.

3.  Right-click the selection to uninstall the application.  
      
    ![Lync Dialog Listener Control Panel](images/Dn439305.lync_sdn_api_control_panel(Office.15).png "Lync Dialog Listener Control Panel")  
      
    The uninstall step will automatically stop the Lync Dialog Listener service.

## Uninstall the Lync SDN Manager (LSM)

To uninstall the LSM, follow these steps:

1.  On the LSM server, launch Control Panel to open Program and Features.

2.  Select Microsoft Lync SDN Manager.

3.  Right-click the selection to uninstall the application.

