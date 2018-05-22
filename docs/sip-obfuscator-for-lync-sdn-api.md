---
title: SIP Obfuscator for Lync SDN API
TOCTitle: SIP Obfuscator for Lync SDN API
ms:assetid: 891e4ef9-8763-41fa-ac5b-ce85fa15a13a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439306(v=office.15)
ms:contentKeyID: 57261042
ms.date: 07/24/2014
mtps_version: v=office.15
---

# SIP Obfuscator for Lync SDN API


_**Applies to:** Lync 2013 | Lync Server 2013_

This section describes a utility that is available for the Lync SDN API 2.0.

## Utilities for Lync SDN API

The Lync SDN API 2.0 comes with a utility (SIPObfuscator.exe) that can be used to obtain the obfuscated value of a user name. The resultant obfuscated name can be used to query for dialog data involving the specified user when privacy protection is turned on.

### SIP Obfuscator

When privacy protection is turned on, any personal identifiable information in Lync network diagnostic data will be obfuscated. This means that any user identity will be replaced by an alias. For example, the SIP Uri of sip:adama@contoso.com may be replaced by sip:CE6AF05C9705A05E@contoso.com. When the network traffic patterns of an individual user needs to be specified in this situation, the SIP Obfuscator utility is provided to determine the obfuscated user identity (alias) for an explicit user identity.

SIP Obfuscator is a Windows console application. It is is installed as part of the Lync SDN API 2.0 installation and can be found in the installation directory. By default, the path to this directory is C:\\Microsoft Files\\Microsoft Lync Server\\Microsoft Lync SDN API on a 64-bit machine.

To use SIP Obfuscator, do the following:

1.  Select a known user name, say, adama

2.  Type the following command in a Windows console and hit carriage return.  
    SIPObfuscator adama

3.  The obfuscated user name will be displayed as output, for example:  
    CE6AF05C9705A05E

To search for the data records associated with this user (sip:adama@contoso.com), you can search for the records containing sip:CE6AF05C9705A05E@contoso.com. An example of such an obfuscated data record is shown as follows:

    <StartOrUpdate Type="audio">
        <From>
          <Id>87c1bcf104</Id>
          <EPId>1579d442a7</EPId>
          <URI>sip:CE6AF05C9705A05E@contoso.com</URI>
          ……
        </From>
    </StartOrUpdate>

