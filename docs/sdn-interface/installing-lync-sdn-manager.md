---
title: Installing Lync SDN Manager
TOCTitle: Installing Lync SDN Manager
ms:assetid: 94f85cd3-3ac4-4b61-96cf-5dccb93a4a02
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785203(v=office.15)
ms:contentKeyID: 62952694
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Installing Lync SDN Manager

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

To install Lync SDN Manager:

1.  Copy the LyncSDNManager.msi package to the server computer hosting LSM.

2.  Choose the LyncSDNManager.msi to launch the installation.

3.  In the **Welcome to the Microsoft Lync SDN Manager Setup Wizard**, choose **Next**.

4.  Accept the **End-User License Agreement** and then choose **Next**.

5.  In the **Destination Folder** panel, keep the default or enter a custom LSM installation directory. Do the same for the service logging directory.  
      
    ![Lync SDN Manager destination folder dialog box](images/Dn785203.LSM_dest_folder(Office.15).png "Lync SDN Manager destination folder dialog box")  

6.  In **Lync SDN Manager Topology**, select one of the following options: **Join (or create) a pool of SDN Managers**, **Set up a single SDN Manager that shares its settings with other SDN Managers**, or **Set up a single SDN Manager that does not share settings**.  
      
    ![Lync SDN Manager Topology](images/Dn785203.lync_sdni_lsm_topo(Office.15).png "Lync SDN Manager Topology")  

7.  Depending on the choice that you select, choose one of the following:
    
    1.  If one of the first two options is selected, do the following:
        
          - In **Lync SDN Manager Database Settings**, enter a SQL server name and database instance name, if appropriate, in the **Database Server:** field (for example, LyncSdn\\monitoring). Select either the **Integrated Security** or **SQL Authentication** option as the credentials that the LSM uses to access the database. Make sure to use the credentials with the sufficient privileges to access, create and configure the database. Then choose **Next**.  
              
            ![Lync SDN Interface Database Settings](images/Dn785203.lync_sdni_lsm_dbsettings(Office.15).png "Lync SDN Interface Database Settings")  
        
          - After the installer has successfully contacted the database server, it will either create a new SDN Manager database or connect to an existing one successfully. Choose **Next**.
            

            > [!NOTE]
            > All the LSMs in the pool must be consistently configured with either Integrated Security or the same SQL user.

    
    2.  For the first LSM installation, as well as any independent alternative, in any given deployment, you must specify the submitUri for the LSM instances to post message to the network controllers. In a pooled configuration, other LSMs joining the same LSM pool will retrieve the submitUri value from the shared database. To set the submitUri:
        
          - In **Network Controller Settings**, keep the default or configure the network controller URIs, its controlling subnets and domains, and choose **Next**.
            
            ![Lync SDN Network Controller Settings](images/Dn785203.lync_sdni_network_controller_settings(Office.15).png "Lync SDN Network Controller Settings")
            
            If you chose **Configure** in the previous step, set one or more network controller service URIs in the **Network Controller Configuration** panel. You can also specify the subnets to filter out the traffic from the specified subnets or domain, as well as the client certificates to use.  
              
            ![Lync SDN network controller configuration](images/Dn785203.lync_sdn_interface_network_controller_configuration(Office.15).png "Lync SDN network controller configuration")  
            
            The network controller URI defines the service endpoint for where the LSM locates a specific web service for the network controller to receive the Lync call and quality data. By default, all configured network controllers receive all messages but in practice each network controller is limited to control a particular set of subnets and, possibly, SIP domains. To better target messages only to network controllers that can use particular messages, on this panel you can further define the list of subnets and/or domains for a network controller.
            
            If you use mutual TLS authentication, this panel enables you to select a client certificate to use for each network controller. The same set of client certificates must be installed on each LSM.
        
          - Choose **Ok** to return to the **Network Controller Settings** panel that also displays the resultant submitUri value.
            
            ![Lync SDNI Network Controller Settings Configured](images/Dn785203.lync_sdni_lsm_ncsettings_configured(Office.15).png "Lync SDNI Network Controller Settings Configured")
        
          - Click **Next** to continue.

8.  In the **Ready to install** panel, click the Install button to start the installation.

9.  In the wizard completed panel, click **Finish** to exit the installation wizard.

## See also

- [Installing Lync SDN Manager](installing-lync-sdn-manager.md)
- [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

