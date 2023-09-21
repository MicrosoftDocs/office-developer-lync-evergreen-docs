---
title: Cleaning up Lync SDN Interface 2.1.1
TOCTitle: Cleaning up Lync SDN Interface 2.1.1
ms:assetid: 54465ebc-dbf3-4788-9326-bb1cd34427fd
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785220(v=office.15)
ms:contentKeyID: 62952704
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Cleaning up Lync SDN Interface 2.1.1

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

This section describes how to clean up the LDL and LSM services.

Cleaning up the Lync SDN Interface 2.1.1 involves removing the registration of LDL as a Lync Server application, and uninstalling the Lync Dialog Listener and Lync SDN Manager services.

## Uninstall the Lync Dialog Listener (LDL)

1.  On the LDL server, start Control Panel to open Program and Features.

2.  Select Lync SDN Interface 2.1.1.

3.  Right-click the selection to uninstall the application.  
      
    ![Uninstall LDL and LSM](images/Dn785220.lync_sdni_ldl_uninstall(Office.15).png "Uninstall LDL and LSM")  
      
    The uninstall step will automatically stop the Lync Dialog Listener service.

## Unregister Lync Dialog Listener as Lync server application

To unregister Lync Dialog Listener as a Lync Server application, run the Remove-CsServerApplication cmdlet following these steps:

1.  Start a Lync Server Management Shell window and then issue the following cmdlet:

2.  Issue the following cmdlet:  
      
    ```powershell
    Remove-CsServerApplication -Identity <app identity> 
    ``` 
      
    Where \<app identity\> is the application identity string. For example, "Service:registrar:pool1.contoso.com/Diagnostics". You can follow the example shown in [Installing Lync SDN Interface 2.1.1](installing-lync-sdn-interface-2-1-1.md) to use Get-CsServerApplication cmdlet to find out the \<app identity\> of the application.

3.  After uninstalling all installations of the Lync Dialog Listener you also have to manually remove the registration with the Lync Server.
    
    > [!NOTE]
    > Removing the registration will deactivate any Lync Dialog Listeners on any front-ends deployed in this pool.

## Uninstall the Lync SDN Manager (LSM)

To uninstall the LSM, follow these steps:

1.  On the LSM server, start Control Panel to open Program and Features.

2.  Select Microsoft Lync SDN Manager.

3.  Right-click the selection to uninstall the application.

