---
title: Using SIP Obfuscator for Lync SDN Interface
TOCTitle: Using SIP Obfuscator for Lync SDN Interface
ms:assetid: d71f5c20-627e-43ed-8127-53e0d1c193ad
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785221(v=office.15)
ms:contentKeyID: 62952705
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Using SIP Obfuscator for Lync SDN Interface


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

The Lync SDN Interface 2.1.1 includes a utility (SIPObfuscator.exe) for authorized partners that can be used to obtain the obfuscated value of a user name. The resultant obfuscated name can be used to query for dialog data involving the specified user when privacy protection is turned on. SipObfuscator.exe requires that .NET Framework 3.5 be installed.

## SIP Obfuscator

When privacy protection is turned on, any personal identifiable information in a Lync call and quality data will be obfuscated. This means that any user identity is replaced by an alias. For example, the SIP Uri of sip:adama@contoso.com may be replaced by sip:CE6AF05C9705A05E@contoso.com. When the network traffic patterns of a single user is specified in this situation, the SIP Obfuscator utility is provided to determine the obfuscated user identity (alias) for an explicit user identity.

SIP Obfuscator is a Windows console application. It is installed along with installations of the LSM and LDL.

To use SIP Obfuscator, do the following:

1.  Select a known user name, for example, adama.

2.  Type the following command in a Windows console and press Enter.  
    SIPObfuscator adama

3.  The obfuscated user name is displayed as output, for example:  
    CE6AF05C9705A05E

To search for the data records associated with this user (sip:adama@contoso.com), you can search for the records containing sip:CE6AF05C9705A05E@contoso.com. An example of such an obfuscated data record is shown as follows:

    <Start Type="audio">
        <From>
          <Id>87c1bcf104</Id>
          <EPId>1579d442a7</EPId>
          <URI>sip:CE6AF05C9705A05E@contoso.com</URI>
          ……
        </From>
    </Start>


> [!NOTE]
> <P>IP addresses are never obfuscated in Lync SDN Interface because they are essential information for identifying the streams in the network.</P>


