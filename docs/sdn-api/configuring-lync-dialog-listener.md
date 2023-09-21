---
title: Configuring Lync Dialog Listener
TOCTitle: Configuring Lync Dialog Listener
ms:assetid: 1c2c97c4-d205-4291-8dca-627a94c90d62
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439303(v=office.15)
ms:contentKeyID: 57261039
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Configuring Lync Dialog Listener

**Applies to:** Lync 2013 | Lync Server 2013

> [!NOTE] 
> The steps presented in this section are optional unless you want to modify the default configurations.

The configuration settings affect how the listener service behaves and these options are specified in the LyncDialogListener.exe.config file.

The configuration files are located in the Lync SDN API 2.0 installation directory. By default, the path to this directory is C:\\Program Files\\Microsoft Lync Server\\Microsoft Lync SDN API\\.

![The configuration files are located in the Lync SDN API’s installation directory. By default, the path to this directory is C:\\Program Files\\Microsoft Lync Server\\Microsoft Lync SDN API\\.](images/Dn439303.lync_sdn_api_installation_directory(Office.15).png "The configuration files are located in the Lync SDN API’s installation directory. By default, the path to this directory is C:\\Program Files\\Microsoft Lync Server\\Microsoft Lync SDN API\\.")

The following section describes how to configure Lync Dialog Listener.

## Configure Lync Dialog Listener logging options

Follow these steps to modify the Lync Dialog Listener logging configuration.

1. Navigate to the API installation directory.

2. Open the LyncDialogListener.exe.config file with a text editor.

3. Search for the \<loggingConfiguration\> section and make appropriate changes to entries under the \<Listeners\> elements.


> [!NOTE]
> The configuration file can be conveniently inspected and modified using the Microsoft Enterprise Library Configuration Tool. For more information, see [Microsoft Enterprise Library](http://msdn.microsoft.com/library/ff648951.aspx).

Each entry (an \<add\> element) under \<listeners\> corresponds to a specified type of logging. Modifications can include adding a new \<add\> entry to enable the specified type of logging, removing an \<add\> entry to disable the specified type of logging, and changing an existing \<add\> entry to modify the specified type of logging.

The Lync Dialog Listener service default configuration supports the following types of logging:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Logging type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>LNEAppLog</p></td>
<td><p>Logging the application execution states, including Debug, Info, and Error types of data. The output is recorded in the LyncDiagnostics.log file.</p></td>
</tr>
<tr class="even">
<td><p>AllDataLog</p></td>
<td><p>Logging all types of data, including SIP messages with SDP headers, quality of experience data and error messages when errors are detected by Lync Dialog Listener.</p></td>
</tr>
<tr class="odd">
<td><p>QoEInputDataLog</p></td>
<td><p>Logging the quality of experience raw data from the Lync Server and error messages when errors are detected while the QoE report is processed.</p></td>
</tr>
<tr class="even">
<td><p>DialogDataLog</p></td>
<td><p>Logging the dialog data, including SIP messages and some SDP headers and error messages when errors are detected while the SIP dialog event is processed.</p></td>
</tr>
</tbody>
</table>

The following example shows the LNEAppLog type of logging options containing a modified logging file path (in the boldface text).

```xml
    <listeners>
      <add name="LNEAppLog"
    type="…" 
    listenerDataType="…" 
    fileName="C:\logdir\LyncDiagnostics.log" 
    footer="" 
    formatter="LNEDetailFormatter" 
    header="" 
    rollFileExistsBehavior="Increment" 
    rollInterval="Day" 
    rollSizeKB="1000000" 
    traceOutputOptions="LogicalOperationStack, 
    DateTime, Timestamp, ProcessId, ThreadId, Callstack"/>
    </listeners>
```

By default, the LyncSDNAPI.msi will set logging levels to be in release mode. To turn on debug mode, you'll need to change the configuration setting. To increase the logging level for debugging purposes, change the following switchValue option from under the \<categorySources\> in the LyncDialogListener.exe.config file. For example to turn off logging, set the switchValue option to "Off", as shown as follows:

```xml
    <add switchValue="Off" name="Debug">
            <listeners>
              <add name="LNEAppLog" />
            </listeners>
        </add>
```

To activate logging for debugging, set the switchValue option to "All" as shown as follows:

```xml 
<add switchValue="All" name="Debug">
        <listeners>
          <add name="LNEAppLog" />
        </listeners>
    </add>

```

## Configure Lync Dialog Listener execution options

Follow these steps to modify the Lync Dialog Listener (LDL) execution configuration.

1.  Navigate to the API installation directory.

2.  Open the LyncDialogListener.exe.config file with a text editor.

3.  Search for the \<appSettings\> section and make appropriate changes to relevant entries therein.

The configuration for executing the LDL service is flexible. The following table shows a few options, as an illustration.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Default configuration</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;add key=&quot;submituri&quot; value=&quot;http://yourSDNManager:9333/LDL/CallInfo&quot; /&gt;</p></td>
<td><p>Set the value of the web address for the LSM. The string value &quot;yourSDNManager&quot; is a placeholder and you should replace it with the name of your SDN manager. This is populated by the installer but can be updated through this configuration.</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;alternatesubmituri&quot; value=&quot;http:// yourSecondarySDNManager:9333/LDL/CallInfo&quot; /&gt;</p></td>
<td><p>Set the value of the web address for the alternate LSM that should be used for failover. You should replace &quot;yourSecondarySDNManager&quot; with the name of your secondary SDN manager.</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;hidepii&quot; value=&quot;true&quot; /&gt;</p></td>
<td><p>Set the value attribute to true to hide personal identifiable information (PII). Set value to false to see PII</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;sendallcallqoe&quot; value=&quot;false&quot; /&gt;</p></td>
<td><p>Set value to false to receive QoE information only for bad calls. Set value to true to see QoE information for all calls.</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;sendrawsdp&quot; value=&quot;false&quot;/&gt;</p></td>
<td><p>Set value to false to not forward any SDP info (the &quot;RawSDP&quot; tag shown above) package. Set value to true to send SDP packages</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;sendcallinvites&quot; value=&quot;false&quot;/&gt;</p></td>
<td><p>Set value to false to not notify about an upcoming call as indicated with an INVITE message. This event precedes a StartOrUpdate event which is initiated by a 200 OK for the SIP INVITE. Set value to true to send INVITE messages.</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;clientcertificateid&quot; value=&quot;&quot;/&gt;</p></td>
<td><p>Set value to a thumbprint of the certificate to use for client certificate authentication.</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;sendmeetingroominfo&quot; value=&quot;false&quot; /&gt;</p></td>
<td><p>Set the value attribute to &quot;true&quot; to see Lync Meeting Room endpoint related information. Otherwise, Lync Meeting Rooms will not be specifically identified.</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;qoedatabasename&quot; value=&quot;&quot; /&gt;</p></td>
<td><p>Set value to the name of QoE database from which thresholds for bad Lync calls are received. If a database name is entered here, Lync SDN API will use the database-defined thresholds. Otherwise, threshold values are also specified in the LyncDialogListener.exe.config file.</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;qoedatabaseusername&quot; value=&quot;&quot; /&gt;</p></td>
<td><p>Set value to the user name for signing in to the QoE database as specified in the database setting above. Windows credentials of the user account running Lync Dialog Listener will be used to access the database. In a trusted connection, set value to an empty string and the credentials of the current user will be used to access the QoE database.</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;qoedatabaseuserpassword&quot; value=&quot;&quot; /&gt;</p></td>
<td><p>Set value to the password of the user above as part of the credentials to log in to the QoE database. In a trusted connection, set value to an empty string.</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;qualitythresholdlevel&quot; value=&quot;Acceptable&quot; /&gt;</p></td>
<td><p>Set value to either Acceptable or Optimal as the threshold for defining poor quality records. The values are defined in the QoE database. By default, Lync Dialog Listener uses the Acceptable level to identify bad QoE quality.</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;submitqueuelen&quot; value=&quot;100&quot; /&gt;</p></td>
<td><p>Set value to the maximum unanswered and waiting messages to send to LSM. Change this value only if network conditions require a longer queue length due to delays in messages being received.</p></td>
</tr>
</tbody>
</table>

The following example shows an excerpt of a Lync Dialog Listener execution configuration, specifying where (submituri) to post the diagnostic data (sendrawsdp, sendallcallqoe, sendmeetingroominfo), how to submit the data, and what quality of experience metrics (qualityThresholdLevel, audio-DegradationAvgOptimal, audio-DegradationAvgAcceptable) to use in provisioning of the Lync network diagnostic data to a network management system.

```xml
    <appSettings>
        <add key="submituri" value="http://www.contoso.com/SDNWebService/PostStuffHere" />
        <add key="hidepii" value="true" />
        <add key="sendrawsdp" value="true" />
        <add key="sendallcallqoe" value="true" />
        <add key="sendmeetingroominfo" value="true" />
    
        <add key="qualitythresholdlevel" value="Acceptable" />
    
        <add key="audio-DegradationAvgOptimal" value="0.6" />
        <add key="audio-DegradationAvgAcceptable" value="1" />
    ……
      </appSettings>
```

At the bottom of the configuration file is a list of optional Quality of Experience fields which can be changed to customize individual threshold levels. These by default match the default values of thresholds within the Quality of Experience database. The full list of these fields is as follows:

```xml
    <add key="audio-DegradationAvgOptimal" value="0.6" />
        <add key="audio-DegradationAvgAcceptable" value="1" />
        <add key="audio-RoundTripOptimal" value="200" />
        <add key="audio-RoundTripAcceptable" value="500" />
        <add key="audio-PacketLossRateOptimal" value="0.02" />
        <add key="audio-PacketLossRateAcceptable" value="0.05" />
        <add key="audio-JitterInterArrivalOptimal" value="15" />
        <add key="audio-JitterInterArrivalAcceptable" value="25" />
        <add key="audio-RatioConcealedSamplesAvgOptimal" value="0.03" />
        <add key="audio-RatioConcealedSamplesAvgAcceptable" value="0.07" />
        <add key="audio-RatioStretchedSamplesAvgOptimal" value="1" />
        <add key="audio-RatioStretchedSamplesAvgAcceptable" value="1" />
        <add key="audio-RatioCompressedSamplesAvgOptimal" value="1" />
        <add key="audio-RatioCompressedSamplesAvgAcceptable" value="1" />
        <add key="audio-DeviceHalfDuplexAECEventRatioOptimal" value="0.1" />
        <add key="audio-DeviceHalfDuplexAECEventRatioAcceptable" value="0.3" />
        <add key="audio-DeviceRenderNotFunctioningEventRatioOptimal" value="0.1" />
        <add key="audio-DeviceRenderNotFunctioningEventRatioAcceptable" value="0.3" />
        <add key="audio-DeviceCaptureNotFunctioningEventRatioOptimal" value="0.1" />
        <add key="audio-DeviceCaptureNotFunctioningEventRatioAcceptable" value="0.3" />
        <add key="video-CallType" value="1" />
        <add key="video-VideoPostFECPLROptimal" value="0.05" />
        <add key="video-VideoPostFECPLRAcceptable" value="0.1" />
        <add key="video-VideoLocalFrameLossPercentageAvgOptimal" value="5" />
        <add key="video-VideoLocalFrameLossPercentageAvgAcceptable" value="10" />
        <add key="video-RecvFrameRateAverageOptimal" value="12" />
        <add key="video-RecvFrameRateAverageAcceptable" value="7" />
        <add key="video-LowFrameRateCallPercentOptimal" value="5" />
        <add key="video-LowFrameRateCallPercentAcceptable" value="10" />
        <add key="video-LowResolutionCallPercentOptimal" value="5" />
        <add key="video-LowResolutionCallPercentAcceptable" value="10" />
        <add key="video-VideoPacketLossRateOptimal" value="0.05" />
        <add key="video-VideoPacketLossRateAcceptable" value="0.1" />
        <add key="video-VideoFrameRateAvgOptimal" value="12" />
        <add key="video-VideoFrameRateAvgAcceptable" value="7" />
        <add key="video-DynamicCapabilityPercentOptimal" value="5" />
        <add key="video-DynamicCapabilityPercentAcceptable" value="10" />
        <add key="applicationsharing-CallType" value="1" />
        <add key="applicationsharing-AppliedBandwidthLimitOptimal" value="1000000" />
        <add key="applicationsharing-AppliedBandwidthLimitAcceptable" value="500000" />
        <add key="applicationsharing-SpoiledTilePercentTotalOptimal" value="11" />
        <add key="applicationsharing-SpoiledTilePercentTotalAcceptable" value="36" />
        <add key="applicationsharing-JitterInterArrivalOptimal" value="50" />
        <add key="applicationsharing-JitterInterArrivalAcceptable" value="100" />
        <add key="applicationsharing-RelativeOneWayBurstDensityOptimal" value="1000" />
        <add key="applicationsharing-RelativeOneWayBurstDensityAcceptable" value="2000" />
        <add key="applicationsharing-RDPTileProcessingLatencyBurstDensityOptimal" value="100" />
        <add key="applicationsharing-RDPTileProcessingLatencyBurstDensityAcceptable" value="200" />
        <add key="applicationsharing-RelativeOneWayAverageOptimal" value="1" />
        <add key="applicationsharing-RelativeOneWayAverageAcceptable" value="1.75" />
        <add key="applicationsharing-RDPTileProcessingLatencyAverageOptimal" value="200" />
        <add key="applicationsharing-RDPTileProcessingLatencyAverageAcceptable" value="400" />
```
