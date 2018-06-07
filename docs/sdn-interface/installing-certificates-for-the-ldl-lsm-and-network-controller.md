---
title: Installing certificates for the LDL, LSM and network controller
TOCTitle: Installing certificates for the LDL, LSM and network controller
ms:assetid: 840474e7-94ee-4ea1-8bf4-64a168adfeea
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785201(v=office.15)
ms:contentKeyID: 62952685
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Installing certificates for the LDL, LSM and network controller


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

**In this article**  
Installing the trusted root certificate  
Installing certificates for use with Lync SDN Manager over SSL  
Installing certificates for use with the Lync Dialog Listener over SSL  
Installing server certificate on network management system  
Installing client certificate on an LSM host  
Additional resources  

To help to ensure secure message transport and client authentication, the Lync SDN Interface components support mutual TLS. For this to work, you must request certificates from a certification authority (CA) for use over SSL with the LSM and the LDL. You might have to install a root certificate of the CA if it is not trusted. In addition, you must install a server certificate on the network controllers and a client certificate on the LSM host computer.

In the following procedures, assume that a Microsoft Certification Authority is being used and then summarizes the steps necessary to request and install a certificate. For detailed explanation and instructions on how to create a certificate request for Microsoft Certificate Services, see [Managing Certificate Services and SSL](http://technet.microsoft.com/en-us/library/bb727098.aspx).

## Installing the trusted root certificate


> [!NOTE]
> <P>The procedure is necessary only if you are notified that the CA is not trusted, which can occur when you use a private or custom certificate server instead of acquiring certificates from an established public CA.</P>



To install the root certificate of a CA:

  - In your web browser, navigate to your local certification server. This should be the same CA used for generating the server and, optionally, client certificates.

  - Choose Download a CA certificate, certificate chain, or CRL link, as needed.

  - Select the appropriate CA from the list and choose the Base 64 Encoding Method.

  - Choose the **Download CA certificate** link and then choose the **Open** option when you are prompted to open or save the certificate.

  - When the certificate window opens, choose **Install Certificate…**. The Certificate Import Wizard appears.

  - Choose **Next**, and when you are prompted for the Certificate Store, choose **Place all certificates in the following store**. Then, browse to select the Trusted Root Certification Authorities store.

  - Complete the remaining steps of the wizard.

  - Start MMC and add the certificate snap-ins:
    
    1.  Start the Microsoft Management Console (mmc.exe).
    
    2.  Choose **File** \> **Add/Remove Snap-ins**.
    
    3.  Select **Certificates** and then choose **Add**.
    
    4.  Choose **My user account**.
    
    5.  Choose **Add** again and select **Computer Account**.

  - Move the new certificate from the **Certificates-Current User** \> **Trusted Root Certification Authorities** to **Certificates (Local Computer)** \> **Trusted Root Certification Authorities**.

## Installing certificates for use with Lync SDN Manager over SSL

You must install certificates in order to:

  - Authenticate and secure communications between possibly multiple LDLs and a LSM.

  - Authenticate and secure communications from LSM to possibly multiple network management systems (i.e., network controllers.)

You should follow the standard WCF certificate validation mechanism to configure the settings to validate the client certificate.

For Lync SDN Manager (LSM) to post the call and quality data to the network management system using HTTPS over SSL, an X.509 server certificate must be installed on the network management system. In addition, the network management system might require that LSM present a client certificate to be authenticated. For such operations, the network management system acts as a server and LSM as a client. Both ends of each communication must have a certificate for mutual authentication. For SSL, at least the server-side certificate is required.

Each server certificate must contain a FQDN of the network management system. An IP address, host name or local addresses (\*.local) cannot be used. The certificate must be installed in the local computer store. When client authentication is required, the client certificate might need to contain a FQDN of the computer that is hosting LSM, depending on how the server authenticates a client. The certificates must be signed by a CA trusted by all involved parties. When a CA is not trusted, the root certificate of this CA must be installed on all involved computers.

To install certificates:

1.  Request a certificate from a certificate server.

2.  Install the server certificate on a network management system.

3.  Install the client certificate on all the servers on which LSM runs, if client authentication is required by the network management system.

4.  Install a trusted root certificate, when the CA is reported as not being trusted.

## Installing certificates for use with the Lync Dialog Listener over SSL

To install certificates required by the Lync Dialog Listener (LDL), follow the instructions from the Installing Certificates for Use with Lync SDN Manager over SSL section. More specifically, the client certificates should be installed on the LDL servers, and the server certificates should be installed on the Lync SDN Manager (LSM) servers. In this manner, the LDL servers are considered clients of the LSM servers, which in turn are clients of the Network Management System.

## Installing server certificate on network management system


> [!NOTE]
> <P>Make sure the Network Management System is assigned an FQDN, e.g., "netman.contoso.com". This should have at least one period delimiter (".").</P>



To install the server certificate on a Windows-based network management system:

1.  In your web browser, navigate to your certification server. Note: 
    

    > [!NOTE]
    > <P>This should be the same CA used for generating the certificates for the client.</P>



2.  Choose the **Request a certificate** link.

3.  Choose the **Advanced certificate request** link.

4.  Choose the **Create and submit a request to this CA** link.

5.  In the Certificate Template dropdown, select the **Exportable Server Cert** option.

6.  When creating the certificate, specify the FQDN as the Name of the certificate in addition to the Friendly Name. Other fields can remain blank or use their default values.

7.  Choose **Submit**.

8.  Choose the **Install this Certificate** link. The certificate will be installed to the **Certificates-Current User -\> Personal -\> Certificates** folder.

9.  Start MMC and add the certificate snap-ins shown in step 8 of the Install the Trusted Root Certificate section.

10. Move the certificate from the **Certificates-Current User -\> Personal -\> Certificates** to **Certificates (Local Computer) -\> Personal -\> Certificates**.

## Installing client certificate on an LSM host


> [!NOTE]
> <P>This procedure is necessary only if the network management system requires client authentication. In this case, the network controller must be configured to validate and accept the client certificate.</P>
> <P>When generating the client certificate, you must set the parameters and fields according to the certificate validation policy of the network management system.</P>



To install the client certificate, follow the steps listed in the Install server certificate procedure earlier in this article on every Lync SDN Manager.


> [!NOTE]
> <P>To change the LSM configuration via command-line prompt or in the configuration file, you must specify the thumbprint of the installed certificates in the submitUri. Similarly, you must specify the certificate thumbprint in the clientcertificateId field in the LDL configuration. You can, for example, obtain the thumbprint from the Certificate panel, as shown in the following screenshot.</P>



![The thumbprint can be obtained from the Certificate panel](images/Dn785201.lync_sdn_api_install_certificate(Office.15).png "The thumbprint can be obtained from the Certificate panel")

The selected values (without spaces) must be specified in the **clientcertificateid** property of the configuration file of LDL.

\<add key="clientcertificateid" value="a45351e9af8562e7ccd72d2f311ebfe538fca5f7" /\>


> [!NOTE]
> <P>You can verify client authentication works independent of Lync SDN Interface by using a general-purpose test tool, such as wfetch.exe.</P>



## Additional resources

  - [Getting ready to install Lync SDN Interface 2.1.1](getting-ready-to-install-lync-sdn-interface-2-1-1.md)

  - [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

