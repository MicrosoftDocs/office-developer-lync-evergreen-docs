---
title: Configuring Lync SDN Interface 2.1.1 Lync Dialog Listener
TOCTitle: Configuring Lync SDN Interface 2.1.1 Lync Dialog Listener
ms:assetid: 0f604c7d-87a3-4526-b67c-25648c8427e7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785206(v=office.15)
ms:contentKeyID: 62952695
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Configuring Lync SDN Interface 2.1.1 Lync Dialog Listener


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

LDL uses configuration settings to affect how the listener service behaves. LDL requires only minimal explicitly specified configuration. You can set or modify additional LDL configurations by editing the LyncDialogListener.exe.config file. The installation sets all important configurations such as those for connecting to the LSM (submituri, alternativeuri, clientcertificateid, checkdns) as well as the overall logging location.

In general, the Lync Dialog Listener obtains the settings using two mechanisms:

  - From the LyncDialogListener.exe.config file.

  - From the configuration provisioned by the LSM after LDL connects to the LSM.

This section explains how to configure Lync Dialog Listener in the LyncDialogListener.exe.config file. The configuration file is located in the LDL installation directory. By default, the path of this directory is C:\\Program Files\\Microsoft Lync Server\\Microsoft Lync Dialog Listener\\, as is shown in the following screen capture.

![Locating LDL config file](images/Dn785206.lync_sdni_ldl_config_file_location(Office.15).png "Locating LDL config file")


> [!NOTE]
> <P>The instructions in this section are optional unless you want to change the default settings configured by the installer.</P>



## In this section

  - [Configuring LDL logging options](configuring-ldl-logging-options.md)

  - [Configuring LDL execution options](configuring-ldl-execution-options.md)

## See also

  - [Configuring Lync SDN Interface 2.1.1](configuring-lync-sdn-interface-2-1-1.md)

  - [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

