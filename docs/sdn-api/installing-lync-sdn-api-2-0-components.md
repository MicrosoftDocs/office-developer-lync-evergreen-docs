---
title: Installing Lync SDN API 2.0 components
TOCTitle: Installing Lync SDN API 2.0 components
ms:assetid: 1ce71caf-b50f-4d15-b648-90bd0a219de8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439302(v=office.15)
ms:contentKeyID: 57261038
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Installing Lync SDN API 2.0 components

**Applies to:** Lync 2013 | Lync Server 2013

Complete the prerequisites and run the API installation wizard to install the Lync SDN API 2.0.

There are two .msi packages to install the Lync SDN API 2.0: the Lync Dialog Listener (LDL) installer (lyncsdnapi.msi), and the Lync SDN Manager (LSM) installer (lyncsdnmanager.msi).

## Before you install the LDL

The following prerequisistes must be met before the LDL can be installed and started successfully:

1. Service Control Panel is closed on all Lync Server host machines where this application will be installed.

2. The LyncSDNAPI.msi installer must be run on a Lync Server front end role from an administrator account that is also a part of the RTC Server Applications local group. If not, perform the following:
    
    1. Login to the Lync Server front end server computer as the administrator and launch the Server manager snap-in.
    
    2. Add the administrator account to to the RTC Server Applications local group.
    
      > [!NOTE]
      > If this is the first time running steps 2a and 2b, log out and log back in for the changes to take effect.

3.  The LSM installer should be installed on a separate application server so as to maximize the performance of the Lync Server Front End.

4.  Note the URI for the LSM to have it ready for the LDL installation. Both LDL and LDL logging configuration are combined in the single dialoglistener.exe.config file. Note: Logging with the LDL is configured during the installation process, so editing the config file for logging is not required.

5.  Configure LSM config files (LyncSDNManager.exe.config) on the LSM, and secondary if exists, to send to the URI of the network management system. Note: Logging with the LSM is configured during the installation process, so editing the config file for logging is not required.

## Run the LDL Installation Wizard

Follow these steps to use the Lync SDN API 2.0 Setup Wizard to install the Lync SDN API 2.0:

1.  Copy the LyncSDNAPI.msi package to each Lync Server front end and open the installation package on each front end.

2.  To start setup, double-click the .msi. In the Welcome to the Microsoft Lync SDN API Setup Wizard, click **Next**.  
      
    ![Welcome to the MS Lync SDN API Setup Wizard](images/Dn439302.lync_sdn_api_wizard_1(Office.15).png "Welcome to the MS Lync SDN API Setup Wizard")  

3.  Accept the End-User License Agreement and then click **Next**.  
      
    ![Lync SDN API Setup End User License Agreement](images/Dn439302.Lync_SDN_Wizard_EULA(Office.15).png "Lync SDN API Setup End User License Agreement")  

4.  Specify the installation folder or use the default installation path. Click **Next**.  
      
    ![Specify the installation folder](images/Dn439302.lync_sdn_api_wizard_2(Office.15).png "Specify the installation folder")  

5.  Specify your primary SDN manager Uri, optionally a secondary SDN manager Uri, and a path to a directory to which logs will be written. Click **Next**.  
      
    ![Install SDN API Settings](images/Dn439302.InstallSdnApiSettings(Office.15).png "Install SDN API Settings")  
      
    If the secondary SDN manager Uri is not set in this step, you must specify it by editing the LDL configuration file.  
      

6.  In the **Choose the Account Type for the Lync Dialog Listener** popup window, select either User **Network Service Account** or **Enter Account Credentials** option. Click **Next**.  
      
    ![Install Lync SDN API Settings: Choose Account Type](images/Dn439302.InstallLyncSDNApiChooseAccountType(Office.15).jpg "Install Lync SDN API Settings: Choose Account Type")  
      
    When **Enter Account Credential option** is selected, you will then be prompted to enter the credentials of a Lync account belonging to the RTC Server Applications local group.  
      

7.  In the **Ready to install** panel, click the **Install** button to start the installation.  
      
    ![Click the Install button to start the installation](images/Dn439302.lync_sdn_api_wizard_5(Office.15).png "Click the Install button to start the installation")  

8.  In the wizard completed panel, click **Finish** to exit the installation wizard.  
      
    ![Click Finish to exit the installation wizard](images/Dn439302.lync_sdn_api_wizard_6(Office.15).png "Click Finish to exit the installation wizard")  

## Install the LSM

1.  Copy the LyncSDNManager.msi package to the server that will act as the LSM role.

2.  To start setup, double-click the .msi. In the Welcome to the Microsoft Lync SDN Manager Setup Wizard, click **Next**.  
      
    ![Lync SDN Manager Setup Wizard](images/Dn439302.LSM_setup(Office.15).png "Lync SDN Manager Setup Wizard")  

3.  Accept the End-User License Agreement and then click **Next**.

4.  Specify the installation folder or use the default installation path. Click **Next**.  
      
    ![Lync SDN Manager destination folder dialog box](images/Dn439302.LSM_dest_folder(Office.15).png "Lync SDN Manager destination folder dialog box")  

5.  Enter the Web service address of a contracted network management system that will receive the Lync SDN API 2.0 data, specify the logging directory (or keep the default) where application logs will be saved, and click **Next**.  
    
    > [!NOTE]
    > When multiple Web services are used, their addresses can be specified in the Submit URI field as a space-, comma- (,) or semi-colon-separated string. For example, "http://server1/site1;http://server2/site2".

    
    ![Lync SDN Manager submit URI dialog box](images/Dn439302.LSM_submit_uri(Office.15).png "Lync SDN Manager submit URI dialog box")  

6.  In the Ready to install panel, click the Install button to start the installation.  
      
    ![Lync SDN Manager ready to install dialog box](images/Dn439302.LSM_install(Office.15).png "Lync SDN Manager ready to install dialog box")  

7.  In the wizard completed panel, click Finish to exit the installation wizard.  
      
    ![Lync SDN Manager completed setup dialog box](images/Dn439302.LSM_finish(Office.15).png "Lync SDN Manager completed setup dialog box")  

## Install certificates for use with Lync SDN Manager over SSL

Installing certificates is required for the following purposes:

- To secure communications between possibly multiple LDLs and a LSM.
- To secure communications from LSM to possibly multiple network management systems (or network controllers.)

For Lync SDN Manager (LSM) to post the diagnostic data to the network management system using HTTPS over SSL, an X.509 server certificate must be installed on the network management system. In addition, the network management system may or may not require that LSM present a client certificate to be authenticated. In such operations, the network management system acts as a server and LSM as a client.

Each server certificate must contain a FQDN of the network management system. An IP address, host name or local addresses (\*.local) cannot be used. The certificate must be installed in the local computer store. When client authentication is required, the client certificate may need to contain a FQDN of the machine hosting LSM, depending upon how the server authenticates a client. The certificates must be signed by a certificate authority (CA) trusted by all involved parties. When a CA is not trusted, the root certificate of this CA must be installed on all involved machines.

The general steps to install certificates are as follows:

1.  Request a certificate from a certificate server.

2.  Install a trusted root certificate, when the CA is reported as not being trusted.

3.  Install the server certificate on a network management system.

4.  Install the client certificate on the server on which LSM runs, if client authentication is required by the network management system.


> [!NOTE]
> The instructions below assume that the certificates are generated using Microsoft Certificate Services.

### Request a certificate from Microsoft Certificate Services

For instructions on how to create a certificate request for Microsoft Certificate Services, see Managing Certificate Services and SSL.

### Install the trusted root certificate

> [!NOTE]
> The procedure is necessary only if you are notified that the certificate authority is not trusted, which can happen when you use a private or custom certificate server instead of acquiring certificates from an established public certificate authority.

Follow the procedure below to install the root certificate of a certificate authority (CA).

1. In your web browser, navigate to your local certification server. This should be of the same CA used for generating the server and, optionally, client certificates.

2. Click the Download a CA certificate, certificate chain, or CRL link, as needed.

3. Select the appropriate CA certificate authority from the list and choose the Base 64 Encoding Method.

4. Click on the **Download CA certificate** link and click the **Open** option when prompted to open or save the certificate.

5. When the Certificate window opens, click the **Install Certificate…** button. The Certificate Import Wizard appears.

6. Click the **Next** button and, when prompted for the Certificate Store, choose **Place all certificates in the following store**. Then, browse to select the Trusted Root Certification Authorities store.

7. Complete the remaining steps of the wizard.

8. Launch MMC and add the certificate snap-ins:
    
    1.  Launch the Microsoft Management Console (mmc.exe).
    
    2.  Click **File** -\> **Add/Remove Snap-ins**.
    
    3.  Select **Certificates** and click the **Add** button.
    
    4.  Chose **My user account**.
    
    5.  Click **Add** again and select **Computer Account**.

9. Move the new certificate from the **Certificates-Current User**INVALID USE OF SYMBOLS **Trusted Root Certification Authorities** to **Certificates (Local Computer)** INVALID USE OF SYMBOLS**Trusted Root Certification Authorities**.

### Install server certificate on network management system

To install the server certificate on a Windows-based network management system, follow the steps below.

> [!NOTE]
> Make sure the Network Management System is assigned an FQDN, e.g., "netman.contoso.com". This should have at least one period delimiter (".").

1.  In your web browser, navigate to your certification server. Note:  This should be of the same CA used for generating the certificates for the client.

2.  Click the **Request a certificate** link.

3.  Click the **Advanced certificate request** link.

4.  Click the **Create and submit a request to this CA** link.

5.  In the Certificate Template dropdown, choose the **Exportable Server Cert** option.

6.  When creating the certificate, make sure to specify the FQDN as the Name of the certificate as well as the Friendly Name. Other fields can remain blank or use their default values.

7.  Click the **Submit** button.

8.  Click the **Install this Certificate** link. The certificate will be installed to the **Certificates-Current User -\> Personal -\> Certificates** folder.

9.  Launch MMC and add the certificate snap-ins as in step 8 of the Install the Trusted Root Certificate section above.

10. Move the certificate from the **Certificates-Current User -\> Personal -\> Certificates to Certificates (Local Computer) -\> Personal -\> Certificates**.

### Install client certificate on Lync SDN Manager (LSM) host

> [!NOTE]
> This procedure is necessary only if the network management system requires client authentication. In this case, . the network controller must be configured to validate and accept the client certificate. When generating the client certificate, the parameters and fields must be set according to the certificate validation policy of the network management system.

To install the client certificate, follow the steps listed in Install server certificate procedure above on every Lync SDN Manager.

> [!NOTE]
> The Thumbprint of the installed certificate must be specified in the LSM’s configuration file. For example, the thumbprint can be obtained from the Certificate panel as shown in the following screenshot:
> 
> ![The thumbprint can be obtained from the Certificate panel](images/Dn785201.lync_sdn_api_install_certificate(Office.15).png "The thumbprint can be obtained from the Certificate panel")

The selected values (without spaces) must be specified in the **clientcertificateid** property of the configuration file of LSM:

`<add key="clientcertificateid" value="a45351e9af8562e7ccd72d2f311ebfe538fca5f7" />`

> [!NOTE]
> You can verify client authentication works independent of Lync SDN API by using a general-purpose test tool, such as wfetch.exe.


## Install certificates for use with the Lync Dialog Listener over SSL

To install certificates required by the Lync Dialog Listener (LDL), follow the instructions from Section 2.4 "Installing Certificates for Use with Lync SDN Manager over SSL" in the following way: The client certificates should be installed on the LDL servers, and the server certificates should be installed on the Lync SDN Manager (LSM) servers. In this way, the LDL servers are considered to be clients of the LSM servers, which in turn are clients of the Network Management System.

## Troubleshoot installation of Lync SDN API

LyncDialogListener.exe is to be run as Lync Server application. As such, it must be properly registered with the Lync Server. When an installation of the Lync SDN API fails, it is possible that LDL is not properly registered. To trouble shoot, you can verify that the application is properly registered by using the Get-CsServerApplication cmdlet from the Lync Server Management Shell.

1. Launch Lync Server Management Shell.

2. Issue the following PowerShell cmdlet in the Lync Server Management Shell window:  
    Get-CsServerApplication

3. Verify the following entry (or a similar one) is displayed in the output of the above cmdlet:  
      
   ![Verify that the following entry (or a similar one) is displayed in the output of the above cmdlet](images/Dn785218.lync_sdn_api_lync_server_mgmt_shell(Office.15).png "Verify that the following entry (or a similar one) is displayed in the output of the above cmdlet")  
      
   If such an entry is not shown in the output, make sure that your are running in a domain administrator account that is also member of the the RTC Server Applications local group.

