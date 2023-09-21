---
title: Installing Lync Dialog Listener
TOCTitle: Installing Lync Dialog Listener
ms:assetid: d3e65c58-3248-4a7d-a7d9-01526c0dcca8
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785202(v=office.15)
ms:contentKeyID: 62952686
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Installing Lync Dialog Listener

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

Follow these steps to use the LDL Setup Wizard to install the Lync SDN Interface 2.1.1:

1. Copy the LyncDialogListener.msi package to each Lync Server front end and run the installation package on each front end as follows.

2. Choose the LyncDialogListener.msi. In the **Welcome to the Microsoft Lync Dialog Listener Setup Wizard**, choose **Next**.

3. Accept the End-User License Agreement, and then choose **Next**.

4. Specify the installation folder or use the default installation path in addition to the location of the application logs. Choose **Next**.  
      
   ![LDL INSTALLATION FOLDER](images/Dn785202.lync_sdni_ldl_install_destination_folder(Office.15).png "LDL INSTALLATION FOLDER")  
    
   The installer will attempt to locate a DNS SRV record referring to an LSM pool and let you choose this SRV record to connect to the LSM. If you use this option, you might be prompted to specify a client certificate and an account under which the LDL Windows Service should run before continuing the installation.

5. In **Lync SDN Topology**, select one of the three options and then choose **Next**.  
      
   ![SDN TOPOLOGY](images/Dn785202.lync_sdni_ldl_install_network_Topology(Office.15).png "SDN TOPOLOGY")  
   With the first choice, the installer expects the LSM to be installed on the same Lync Server Front-End. In this case, there is no need for mutual TLS and you can skip the next step. Choose the second option to connect the LDL with an LSM pool. Use the third option to configure the LDL to connect to two LSMs, one to be considered the primary and the second the alternative LSM in an Active/Standby failover configuration.

6. If you chose the **In a pool and can be addressed with a pool FQDN** or **In an Active/Standby failover configuration** option, perform the following additional steps:
    
   - With the **In a pool and can be addressed with a pool FQDN** option, you can choose to use a DNS SRV record to provide the SDN Manager pool URI and choose a certificate for authentication to use the HTTPS protocol.
        
   > [!NOTE]
   > Before installation, this DNS SRV record does not exist. Make sure that you have added this record before LDL can successfully connect to the LSM pool.

   Alternatively, in the next step, enter the FQDN of the LSM pool that the LDL will connect to.
    
   - With the **In an Active/Standby failover configuration** option, set the primary and secondary SDN Manager URIs and select a certificate for authentication to use the HTTPS protocol.

7. In **Lync Dialog Listener Service Account** panel, select the **Network Service** or **Specify an Account** option, and then select **Next**.  
      
   ![SERVICE ACCOUNT](images/Dn785202.lync_sdni_ldl_install_Service_Account(Office.15).png "SERVICE ACCOUNT")  
    
   This panel allows you to specify a user account to run the LDL Windows Service or using Network Service. If the LDL service fails to start using Network Service, you may need to change the Windows service definition and specify different credentials. Network Service or the specified user account must be in the *RTC Server Applications* or *RTC Local Administrators* local group.

8. In the **Ready to install** panel, choose the **Install** button to start the installation.

9. In the wizard completed panel, choose **Finish** to exit the installation wizard.

## See also

- [Installing Lync SDN Manager](installing-lync-sdn-manager.md)
- [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

