---
title: Activating an auto-provisioned application
TOCTitle: Activating an auto-provisioned application
ms:assetid: 0f3a7547-8118-4b14-b88b-c8f4b5e5f99d
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466123(v=office.15)
ms:contentKeyID: 57103416
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Activating an auto-provisioned application


**Applies to:** Lync 2013 | Lync Server 2013

 

Trusted applications can be provisioned at run time in two distinct ways: by auto-provisioning, which requires a local Central Management Store replica, or by manual provisioning, which does not require a local Central Management Store replica. The recommended way to provision a UCMA-based application is auto-provisioning. With this style of provisioning, applications can auto-discover, auto-provision, monitor, and react to settings that are relevant in an Microsoft Lync Server 2013 environment.

### To activate an auto-provisioned application

1.  Ensure that the computers on which the application will run are joined to the domain on which Lync Server 2013 will run.

2.  Install the Central Management Store replication service.

3.  Enable Central Management Store replication.

4.  Set the certificate so that the Lync Server 2013 topology is aware of the trusted application computer.

The following sections provide the details of these steps.

## Install the Central Management Store replication service

To perform the steps in this procedure, you must be in the Lync Server Administrator role or Trusted Application Operator role on a computer on which Lync Server Management Shell is installed.

### To install the Central Management Store replication service

1.  On the **Start** menu, select **All Programs**, select **Accessories**, and then right-click **Command-Prompt**, then click **Run as administrator**.

2.  Run Bootstrapper.exe from the Lync Server 2013 core components installation directory by entering the following command.
    
    "%ProgramFiles%\\Microsoft Lync Server 2013\\Deployment\\Bootstrapper.exe" /BootstrapLocalMgmt /MinCache
    

    > [!NOTE]
    > <P>This command installs Microsoft SQL Server 2008 Express, which is required for Central Management Store replication. It also installs Microsoft Visual Studio C++ 2012 Redistributable - x64 (vcredist_x64.exe), SQL Server Native Client (sqlncli.msi), Feature Pack for Microsoft SQL Server 2005 (SQLServer2005_BC.msi), and UcmaRuntime.msi.</P>



## Enable Central Management store replication

This step ensures that the local Central Management Store replica starts getting updates from the master Central Management Store. Before you perform any of the following steps, make sure that you are logged on to the trusted application computer as a domain user/administrator with appropriate privileges. If you are logged in as a local administrator, the PowerShell cmdlets will be unable to work, because your computer will not be able to connect to the master Central Management Store. Administrators and developers who intend to build, provision, and configure a UCMA 4.0-based trusted application that runs as a Lync Server 2013 trusted service must be members of the appropriate universal group. Otherwise they will not be able to carry out their intended tasks.

To perform the steps in this procedure, you must be in the Lync Server Administrator role or Trusted Application Operator role on a computer on which Lync Server Management Shell is installed.

### To enable Central Management Store replication

1.  Launch Lync Server Management Shell.
    
    On the **Start** menu, select **All Programs**, select **Microsoft Lync Server 2013**, right-click **Lync Server Management Shell**, and then click **Run as administrator**.

2.  To configure permissions and bootstrap the replica service, run the **Enable-CsReplica** cmdlet.
    
    Enable-CsReplica

3.  Start the replica service using the **Start-Service** cmdlet.
    
    Start–Service Replica

4.  The **Get-CSManagementStoreReplicationStatus** cmdlet can be used to check the status of Central Management Store replication. Monitor the output from this cmdlet until the **UpToDate** property of the computer on which the replica was installed becomes true.
    
    Get-CSManagementStoreReplicationStatus
    
    Replication can take up to five minutes.

5.  If replication does not occur within five minutes, it can be manually triggered using the **Invoke-CSManagementStoreReplication** cmdlet.
    
    Invoke-CSManagementStoreReplication


> [!NOTE]
> <P>If replication has not successfully completed by application run time, the application throws <STRONG>ProvisioningFailureException</STRONG> on <STRONG>CollaborationPlatform</STRONG> startup.</P>



## Set the certificate

The PowerShell cmdlet in the following procedure enters certificate information into the local Central Management Store. The thumbprint of the certificate can be found by examining the certificate in the Microsoft Management Console Certificates management snap-in and finding the "Thumbprint" key-value pair under the **Details** tab. Remove any spaces from the thumbprint before running the cmdlet.

### To set the certificate

  - Launch Lync Server Management Shell.
    
    On the **Start** menu, select **All Programs**, select **Microsoft Lync Server 2013**, right-click **Lync Server Management Shell**, and then click **Run as administrator**.

  - In Lync Server Management Shell, run the **Set-CsCertificate** cmdlet. In the following example, a certificate with a thumbprint of 14b04424b8316d90c72438dfefdf83d1fd917d39 is bound to the trusted application computer.
    
    Set-CsCertificate -Type Default -Thumbprint 14b04424b8316d90c72438dfefdf83d1fd917d39

This cmdlet must be run for every computer in the pool. This informs UCMA auto-provisioning of the certificate used and also alerts the UCMA platform when the certificate changes.

