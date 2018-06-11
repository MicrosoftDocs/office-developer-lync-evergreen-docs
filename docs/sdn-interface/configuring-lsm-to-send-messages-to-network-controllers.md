---
title: Configuring LSM to send messages to network controllers
TOCTitle: Configuring LSM to send messages to network controllers
ms:assetid: 1e008e31-4054-41f0-a80c-de615364b0f8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785216(v=office.15)
ms:contentKeyID: 62952700
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Configuring LSM to send messages to network controllers

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

LSM sends stream states and quality data to a network controller by posting messages to the URI of a web service on the network controller. You can configure this URI by modifying the submituri setting in the SDNManager.exe.config file.

An LSM can send the messages to multiple network controllers, each having a unique submituri value. You can enable this by setting multiple values on the submituri field. The values must be separated by a semicolon.

You can configure a network controller to receive LSM messages from multiple LSM services. In this case, the different LSM services post messages to the same URI.

Although the submituri value is set by the LSM installer during the installation, this setting can be changed later either by editing the config file or using the SDNManager command line tool to update the database, depending on your deployment scenario.

Set the submitURI by either using a command prompt or editing the SDNManager.exe.config file. For example:
    
- Editing the configuration file:
    
   ```xml
   <add key="submituri" value="10.10.10.0/24,contoso.com=http://localhost:9333/Log/poststuffhere"/>
   ```
    
- Using the command prompt:
    
   `SDNManager.exe /p submituri=10.10.10.0/24,contoso.com=http://localhost:9333/Log/poststuffhere`
    
   or
    
   `SDNManager.exe /p submituri=10.10.11.0/24,redmond.contoso.com,10.10.10.0/24,vienna.contoso.com=http://localhost:9333/Log/poststuffhere;10.10.12.0/24,vienna.contoso.com=http://vienna:8080/network`

When the subnet or domain is not specified, the network controllers receive all messages as in the previous versions of the Lync SDN API.

Multiple routing rules are separated by semicolons and multiple subnets or domains are separated by commas. Spaces are ignored.

