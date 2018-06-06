---
title: Setting up DNS SRV record
TOCTitle: Setting up DNS SRV record
ms:assetid: 1dee6627-bd71-46e9-adb8-f2166fd8a97e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785198(v=office.15)
ms:contentKeyID: 62952682
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Setting up DNS SRV record


_**Applies to:** Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013_

You can configure the Lync Dialog Listener (LDL) to query DNS for the location of the host or pool of the Lync SDN Manager (LSM) Service, if the DNS SRV record was created properly. This article explains how to create the SRV records. You must have domain administrator privileges to do this.


> [!NOTE]
> <P>When DNS "Service Location (SRV)" records are used by LDL, any configured value for the parameter submitURI is ignored. Instead, the URI specified in the SRV record is used.</P>



## To set up the DNS SRV record

1.  Log on to the DNS server and open the DNS Manager

2.  Open **DNS** and choose the zone to create the SRV record for (Current domain, forward lookup zone).

3.  From the Context menu, select **Other New Records...**, navigate to **Service Location (SRV)**, and choose **Create Record**.

4.  Fill in the form (shown in the following figure), specifying \_sdninternal to the **Service:** input box. Enter an FQDN of the host computer (for example, SdnPool.LneProd.contoso.com) to the **Host offering the LSM service**, and select \_http (\_https) in the **Protocol:** field and 9333 (9332) in the **Port number:** input box.
    
    Figure 1. New Resource Record dialog box
    
      
    ![Add DNS SVR records](images/Dn785198.Lync_Sdn_interface_New_resource_record(Office.15).jpg "Add DNS SVR records")
    

    > [!NOTE]
    > <P>If both the HTTP and HTTPS protocols are specified, the HTTP SRV record is ignored until the HTTPS record is deleted.</P>



After the SRV discovery is configured, the following behavior will occur:

If the HTTPS protocol is used, the LDL looks for the **\_sdninternal** service address. Otherwise, the LDL attempts to retrieve the address of an SDN Manager service using the HTTP protocol. It then creates a service URL with the service name ("LDL") appended at the end. An example of the resulting URL is https://SdnPool.LneProd.contoso.com:9332/LDL.

You can enable LDL to check SRV record to discover the LSM locations by selecting the appropriate settings in the LDL Installation Wizard or by editing the LyncDialogListener.exe.config file and setting the following entry.

    <add key="checkdns" value="True"/>

## Additional resources

  - [Getting ready to install Lync SDN Interface 2.1.1](getting-ready-to-install-lync-sdn-interface-2-1-1.md)

  - [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

