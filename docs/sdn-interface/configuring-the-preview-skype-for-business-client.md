---
title: Configuring the Preview Skype for Business Client
TOCTitle: Configuring the Preview Skype for Business Client
ms:assetid: 753f6ff9-d1ff-4770-80f8-f0e71ab92859
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785224(v=office.15)
ms:contentKeyID: 62952707
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Configuring the Preview Skype for Business Client


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

Authorized partners receive access to early editions of our next generation Lync client (Skype for Business), which will provide additional support for SDN in providing additional in-call Quality messages. Currently, only the next major release of Lync client desktop and Modern versions will support sending InCallQuality reports. If you use such a new client, you must activate the in-call feature for LSM to process Incall QoE messages.

After you install the MSI package for the new Lync client, follow the instructions below to examine or enable generating and sending InCallQuality messages the installed new Lync Client.

## Configuring the Lync client for in-call quality reporting in a Lync vNext environment

If you are using a recent preview build of Lync Server vNext as well as the provided preview build of the Lync Client, sending InCallQuality messages will be activated automatically. No manual configuration is necessary. Such newer preview releases of Lync Server will offer a configuration setting to manually activate or deactivate InCallQuality message sending for all connected vNext Lync/Skype for Business clients.

Use the Lync Powershell console and Get/Update-CsMediaConfiguration to verify and change the IncallQuality feature. Access the console by typing the following at the prompt: PS \> Get-CsMediaConfiguration. You will see the following:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Identity</p></td>
<td><p><strong>Global</strong></p></td>
</tr>
<tr class="even">
<td><p>EnableQoS</p></td>
<td><p><strong>False</strong></p></td>
</tr>
<tr class="odd">
<td><p>EncryptionLevel</p></td>
<td><p><strong>RequireEncryption</strong></p></td>
</tr>
<tr class="even">
<td><p>EnableSiren</p></td>
<td><p><strong>False</strong></p></td>
</tr>
<tr class="odd">
<td><p>MaxVideoRateAllowed</p></td>
<td><p><strong>VGA600K</strong></p></td>
</tr>
<tr class="even">
<td><p>EnableInCallQoS</p></td>
<td><p><strong>True</strong></p></td>
</tr>
<tr class="odd">
<td><p>InCalQoSIntervalSeconds</p></td>
<td><p><strong>35</strong></p></td>
</tr>
</tbody>
</table>


The **EnableIncallQoS** attribute will activate/deactivate vNext Lync clients to send raw data necessary for the generation of IncallQuality messages.

The **InCallQoSIntervalSeconds** attribute is used to set the smallest period in which clients will such raw data preventing overburdening the network with additional messages when the stream quality is already impacted.

## Manually Configuring the Lync Client for In-call Quality Reporting

If you are running the latest preview Lync Client with Lync Server 2013, you will need to manually activate each client to support the generation of IncallQuality message. To configure the Preview Lync client for in-call quality reporting, do the following:

1.  Generate the xml configuration file (ocapi\_test.config ) and copy it to the installation path of every new Lync client that contains the Lync.exe (e.g., c:\\program Files\\Microsoft Office\\Office16). The XML file contains the literal content of the ocapi\_test.config file, as follows:
    
      - InCallQosEnabled = true
    
      - InCallQoSPeriodInSec = 35
    
    The literal contents of the ocapi\_test.config file are as follows:
    
    ``` xml
    <?xml version="1.0"?>
    <settings>
        <InCallQosEnabled>true</InCallQosEnabled>
        <InCallQoSPeriodInSec>35</InCallQoSPeriodInSec>
    </settings>
    ```

2.  Restart Lync client by first exiting Lync client (**File** -\> **Exit**) and then restart Lync .

3.  You can change the InCallQoSPeriodInSec to change the maximum frequency of receiving InCallQuality reports from the client and therefore, from the LSM.

