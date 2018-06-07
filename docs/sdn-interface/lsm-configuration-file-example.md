---
title: LSM configuration file example
TOCTitle: LSM configuration file example
ms:assetid: 2113f2b8-80b2-4110-a021-ad7df2d2b517
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn802611(v=office.15)
ms:contentKeyID: 62952712
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# LSM configuration file example


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

The following is an example of the LSM configuration file (SDNManager.exe.config).

## A sample of the SDNManager.exe.config file

``` xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <configSections>
    <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" requirePermission="true"/>
  </configSections>

  <loggingConfiguration name="" tracingEnabled="true" defaultCategory="Error">
    <listeners>
      <add name="LNEAppLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" fileName="C:\Users\ADMINI~1.ENL\AppData\Local\Temp\2\SDN\LyncSDNManager.log" footer="" formatter="LNEDetailFormatter" header="" rollFileExistsBehavior="Increment" rollInterval="Day" rollSizeKB="10000" traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack"/>
      <add name="AllOutputLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" fileName="C:\Users\ADMINI~1.ENL\AppData\Local\Temp\2\SDN\AllOutputManager.log" footer="" formatter="SimpleOutput" header="" rollFileExistsBehavior="Increment" rollInterval="Day" rollSizeKB="10000"/>
      <add name="AllInputLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" fileName="C:\Users\ADMINI~1.ENL\AppData\Local\Temp\2\SDN\AllInputManager.log" footer="" formatter="SimpleOutput" header="" rollFileExistsBehavior="Increment" rollInterval="Day" rollSizeKB="10000"/>
      <add name="ErrorMsgLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" fileName="C:\Users\ADMINI~1.ENL\AppData\Local\Temp\2\SDN\ErrorMsgManager.log" footer="---------------" formatter="LNEDetailFormatter" header="" rollFileExistsBehavior="Increment" rollInterval="Day" rollSizeKB="10000"/>
      <add name="LogOutputLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" fileName="C:\Users\ADMINI~1.ENL\AppData\Local\Temp\2\SDN\LogOutput.log" footer="" formatter="SimpleOutput" header="" rollFileExistsBehavior="Increment" rollInterval="Day" rollSizeKB="10000"/>
      <add name="QoEInputDataLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" fileName="C:\Users\ADMINI~1.ENL\AppData\Local\Temp\2\SDN\QoEInputManager.log" footer="" formatter="SimpleOutput" header="" rollFileExistsBehavior="Increment" rollInterval="Day" rollSizeKB="10000"/>
      <add name="QoEDataLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" fileName="C:\Users\ADMINI~1.ENL\AppData\Local\Temp\2\SDN\QoEDataManager.log" footer="" formatter="SimpleOutput" header="" rollFileExistsBehavior="Increment" rollInterval="Day" rollSizeKB="10000"/>
      <add name="DialogDataLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" fileName="C:\Users\ADMINI~1.ENL\AppData\Local\Temp\2\SDN\DialogData.log" footer="" formatter="SimpleOutput" header="" rollFileExistsBehavior="Increment" rollInterval="Day" rollSizeKB="10000"/>
    </listeners>
    <formatters>
      <add type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" template="{timestamp(local:O)}{tab}{message}{tab}{dictionary({tab}{key}: {value})}" name="LNEOverviewFormatter"/>
      <add type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" template="{timestamp(local:O)}{tab}[{category}]{tab}{message}{tab}{dictionary({tab}{key}: {value})}" name="LNEDetailFormatter"/>
      <add type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" template="{message}{newline}" name="SimpleOutput"/>
    </formatters>
    <categorySources>
      <add switchValue="Off" name="Debug">
        <listeners>
          <add name="LNEAppLog"/>
        </listeners>
      </add>
      <add switchValue="All" name="Error">
        <listeners>
          <add name="LNEAppLog"/>
        </listeners>
      </add>
      <add switchValue="All" name="Info">
        <listeners>
          <add name="LNEAppLog"/>
        </listeners>
      </add>
      <add switchValue="Off" name="QoEInputData">
        <listeners>
          <add name="AllInputLog"/>
        </listeners>
      </add>
      <add switchValue="Off" name="QoEData">
        <listeners>
          <add name="QoEDataLog"/>
        </listeners>
      </add>
      <add switchValue="All" name="RelayData">
        <listeners>
          <add name="LogOutputLog"/>
        </listeners>
      </add>
      <add switchValue="Off" name="DialogData">
        <listeners>
          <add name="AllInputLog"/>
        </listeners>
      </add>
      <add switchValue="All" name="BreakingData">
        <listeners>
          <add name="ErrorMsgLog"/>
        </listeners>
      </add>
      <add switchValue="Off" name="OutputData">
        <listeners>
          <add name="AllOutputLog"/>
        </listeners>
      </add>
      <add switchValue="All" name="TransmissionError">
        <listeners>
          <add name="LNEAppLog"/>
        </listeners>
      </add>
    </categorySources>
    <specialSources>
      <allEvents switchValue="All" name="All Events"/>
      <notProcessed switchValue="ActivityTracing" name="Unprocessed Category">
        <listeners>
          <add name="LNEAppLog"/>
        </listeners>
      </notProcessed>
      <errors switchValue="All" name="Logging Errors &amp; Warnings">
        <listeners>
          <add name="LNEAppLog"/>
        </listeners>
      </errors>
    </specialSources>
  </loggingConfiguration>
  <appSettings>
    <add key="mode" value="Cache"/>
    <!-- Cache, Database, Split - mode how to store call states and settings -->
    <add key="submituri" value="10.12.12.0/24,10.12.13.0/24=http://networkcontroller1.contoso.com/;10.12.14.0/24,Southbranch.contoso.com=[C54CF0D5AC4ED742E3B6B96C76774EC6F863F4D5]https://networkcontroller2.contoso.com/;"/>
    <!-- URI(s) to the network controllers, including subnet and domain restrictions and client certificate - only applicable in cache mode -->

    <add key="statedbserver" value="localhost"/>
    <!-- Database server and credential for accessing call state and settings -->
    <add key="statedbusername" value=""/>
    <!-- empty for integrated security -->
    <add key="statedbpassword" value=""/>

    <add key="calltimeout" value="1.00:00:00"/>
    <!-- 24 hours, max time expected for a call -->
    <add key="invitetimeout" value="0:03:00"/>
    <!-- 3 min, max time expected for ringing -->
    <add key="endedtimeout" value="0:00:15"/>
    <!-- 15 secs, max time expected after call ended to receive first QoE report -->
    <add key="qoetimeout" value="0:00:05"/>
    <!-- 5 secs, max time exepected to receive further QoE reports -->

    <add key="timeouthandlerperiod" value="00:00:01"/>
    <!-- Period to check for call timeouts in the database -->
    <add key="settingsrefresh" value="00:01:00"/>
    <!-- LSM: Period for refreshing the settings from the database (if a database is used to share settings -->
    <add key="maxcachesize" value="1000"/>
    <!-- LSM: maxium number of call states cached (in cache mode) -->

    <add key="quality" value="true"/>
    <!-- Whether to receive additionaly QualityUpdate and IncallQuality messages -->
    <add key="signaling" value="false"/>
    <!-- Whether to receive Invite, Error and Bye messages -->

    <add key="hidepii" value="true"/>
    <!-- Whether to obfuscate user names -->
    <add key="sendrawsdp" value="false"/>
    <!-- Whether to send the raw sdp in Invite and Start/Update messages -->

    <!-- broadcaster parameter -->
    <add key="configurationrefresh" value="00:00:50"/>
    <!-- LDL: Polling period of LDL for configuration updates from the LSM -->
    <add key="submitqueuelen" value="100"/>
    <!-- LDL, LSM: Number of messages buffered in case of transmission issues -->
    <add key="maxretry" value="100"/>
    <!-- LSM,LDL: Maximum number of retrying to send on a connection before the connection is assumed dead -->
    <add key="maxdelaylimit" value="25"/>
    <!-- LSM,LDL: slowing down transmission after this number of transmission failures -->
    <add key="maxbackoff" value="30"/>
    <!-- LSM,LDL max seconds to delay message sending after transmission errors -->
    <add key="maxopen" value="100"/>
    <!-- LSM, LDL: max number of messages being sent concurrently -->
    <add key="maxretrybeforefailover" value="20"/>
    <!-- LDL: max number of messages before attempting to fail over to secondary LSM in Active/Standby configuration  -->

    <!-- Quality thresholds to decide a call being Good (< Optimal), Poor (> Optimal, < Acceptable) or Bad (> Acceptable) -->
    <add key="audio-DegradationAvgOptimal" value="0.6"/>
    <add key="audio-DegradationAvgAcceptable" value="1"/>
    <add key="audio-RoundTripOptimal" value="200"/>
    <add key="audio-RoundTripAcceptable" value="500"/>
    <add key="audio-PacketLossRateOptimal" value="0.02"/>
    <add key="audio-PacketLossRateAcceptable" value="0.05"/>
    <add key="audio-JitterInterArrivalOptimal" value="15"/>
    <add key="audio-JitterInterArrivalAcceptable" value="25"/>
    <add key="audio-RatioConcealedSamplesAvgOptimal" value="0.03"/>
    <add key="audio-RatioConcealedSamplesAvgAcceptable" value="0.07"/>
    <add key="audio-RatioStretchedSamplesAvgOptimal" value="1"/>
    <add key="audio-RatioStretchedSamplesAvgAcceptable" value="1"/>
    <add key="audio-RatioCompressedSamplesAvgOptimal" value="1"/>
    <add key="audio-RatioCompressedSamplesAvgAcceptable" value="1"/>
    <add key="audio-DeviceHalfDuplexAECEventRatioOptimal" value="0.1"/>
    <add key="audio-DeviceHalfDuplexAECEventRatioAcceptable" value="0.3"/>
    <add key="audio-DeviceRenderNotFunctioningEventRatioOptimal" value="0.1"/>
    <add key="audio-DeviceRenderNotFunctioningEventRatioAcceptable" value="0.3"/>
    <add key="audio-DeviceCaptureNotFunctioningEventRatioOptimal" value="0.1"/>
    <add key="audio-DeviceCaptureNotFunctioningEventRatioAcceptable" value="0.3"/>
    <add key="video-VideoPostFECPLROptimal" value="0.05"/>
    <add key="video-VideoPostFECPLRAcceptable" value="0.1"/>
    <add key="video-VideoLocalFrameLossPercentageAvgOptimal" value="5"/>
    <add key="video-VideoLocalFrameLossPercentageAvgAcceptable" value="10"/>
    <add key="video-RecvFrameRateAverageOptimal" value="12"/>
    <add key="video-RecvFrameRateAverageAcceptable" value="7"/>
    <add key="video-LowFrameRateCallPercentOptimal" value="5"/>
    <add key="video-LowFrameRateCallPercentAcceptable" value="10"/>
    <add key="video-LowResolutionCallPercentOptimal" value="5"/>
    <add key="video-LowResolutionCallPercentAcceptable" value="10"/>
    <add key="video-VideoPacketLossRateOptimal" value="0.05"/>
    <add key="video-VideoPacketLossRateAcceptable" value="0.1"/>
    <add key="video-VideoFrameRateAvgOptimal" value="12"/>
    <add key="video-VideoFrameRateAvgAcceptable" value="7"/>
    <add key="video-DynamicCapabilityPercentOptimal" value="5"/>
    <add key="video-DynamicCapabilityPercentAcceptable" value="10"/>
    <add key="applicationsharing-AppliedBandwidthLimitOptimal" value="1000000"/>
    <add key="applicationsharing-AppliedBandwidthLimitAcceptable" value="500000"/>
    <add key="applicationsharing-SpoiledTilePercentTotalOptimal" value="11"/>
    <add key="applicationsharing-SpoiledTilePercentTotalAcceptable" value="36"/>
    <add key="applicationsharing-JitterInterArrivalOptimal" value="50"/>
    <add key="applicationsharing-JitterInterArrivalAcceptable" value="100"/>
    <add key="applicationsharing-RelativeOneWayBurstDensityOptimal" value="1000"/>
    <add key="applicationsharing-RelativeOneWayBurstDensityAcceptable" value="2000"/>
    <add key="applicationsharing-RDPTileProcessingLatencyBurstDensityOptimal" value="100"/>
    <add key="applicationsharing-RDPTileProcessingLatencyBurstDensityAcceptable" value="200"/>
    <add key="applicationsharing-RelativeOneWayAverageOptimal" value="1"/>
    <add key="applicationsharing-RelativeOneWayAverageAcceptable" value="1.75"/>
    <add key="applicationsharing-RDPTileProcessingLatencyAverageOptimal" value="200"/>
    <add key="applicationsharing-RDPTileProcessingLatencyAverageAcceptable" value="400"/>
  </appSettings>

  <system.web>
    <compilation debug="true" targetFramework="4.5"/>
    <httpRuntime targetFramework="4.5"/>
  </system.web>

  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5"/>
  </startup>

  <!--<system.diagnostics>
    <trace autoflush="true" indentsize="4">
      <listeners>
        <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>
      </listeners> 
    </trace>
    <sources>
      <source name="System.Net">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.HttpListener">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Sockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Cache">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.ServiceModel"
                switchValue="Information, ActivityTracing"
                propagateActivity="true">
        <listeners>
          <add name="sdt"
              type="System.Diagnostics.XmlWriterTraceListener"
              initializeData= "c:\logdir\log.e2e" />
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="System.Net" value="Verbose"/>
      <add name="System.Net.Sockets" value="Verbose"/>
      <add name="System.Net.Cache" value="Verbose"/>
      <add name="System.Net.HttpListener" value="Verbose" />
    </switches>
    <sharedListeners>
      <add name="System.Net"
        type="System.Diagnostics.TextWriterTraceListener"
    initializeData="C:\logdir\Tracing.log" traceOutputOptions = "DateTime" />
    </sharedListeners>
  </system.diagnostics>-->

  <system.serviceModel>
    <bindings>
      <webHttpBinding>
        <binding name="wsHttpEndpointBindingNoSec" maxBufferPoolSize="400000" maxReceivedMessageSize="400000" maxBufferSize="400000" transferMode="Streamed">
          <readerQuotas maxDepth="32" maxArrayLength="400000" maxStringContentLength="400000"/>
        </binding>
        <binding name="wsHttpEndpointBinding" maxBufferPoolSize="400000" maxReceivedMessageSize="400000" maxBufferSize="400000" transferMode="Streamed">
          <readerQuotas maxDepth="32" maxArrayLength="400000" maxStringContentLength="400000"/>
          <security mode="Transport">
            <transport clientCredentialType="Certificate"/>
          </security>
        </binding>
        <binding name="wsHttpEndpointBindingNoCert" maxBufferPoolSize="400000" maxReceivedMessageSize="400000" maxBufferSize="400000" transferMode="Streamed">
          <readerQuotas maxDepth="32" maxArrayLength="400000" maxStringContentLength="400000"/>
          <security mode="Transport">
            <transport clientCredentialType="None"/>
          </security>
        </binding>
      </webHttpBinding>
    </bindings>
    <services>
      <service behaviorConfiguration="CustomValidator" name="Microsoft.Rtc.Enlightenment.Hub.LyncHandler">
        <endpoint address="http://localhost:9333/LDL" behaviorConfiguration="webby" binding="webHttpBinding" bindingConfiguration="wsHttpEndpointBindingNoSec" name="ep0" contract="Microsoft.Rtc.Enlightenment.Hub.ILyncHandler"/>
        <endpoint address="https://localhost:9332/LDL" behaviorConfiguration="webby" binding="webHttpBinding" bindingConfiguration="wsHttpEndpointBinding" name="ep1" contract="Microsoft.Rtc.Enlightenment.Hub.ILyncHandler">
          <identity>
            <dns value="ServerSideCert"/>
          </identity>
        </endpoint>
      </service>

      <!--<service name="Microsoft.Rtc.Enlightenment.Hub.LogService">
        <endpoint address="http://localhost:9333/Log" behaviorConfiguration="webby" bindingConfiguration="wsHttpEndpointBindingNoSec"
          binding="webHttpBinding" name="ep1" contract="Microsoft.Rtc.Enlightenment.Hub.ILogService" />
        <endpoint address="https://localhost:9332/Log" behaviorConfiguration="webby" 
          binding="webHttpBinding" bindingConfiguration="wsHttpEndpointBindingNoCert"
          name="ep1" contract="Microsoft.Rtc.Enlightenment.Hub.ILogService">
          <identity>
            <dns value="ServerSideCert" />
          </identity>
        </endpoint>
      </service>-->

    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CustomValidator">
          <serviceCredentials>
            <clientCertificate>
              <authentication certificateValidationMode="Custom" customCertificateValidatorType="Microsoft.Rtc.Enlightenment.Hub.AcceptAndLogValidator, SDNManager"/>
            </clientCertificate>
          </serviceCredentials>
          <!-- To avoid disclosing metadata information, set the values below to false before deployment -->
          <!--<serviceMetadata httpGetEnabled="true" httpsGetEnabled="true"/>-->
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->
          <serviceDebug includeExceptionDetailInFaults="false"/>
        </behavior>
      </serviceBehaviors>
      <endpointBehaviors>
        <behavior name="webby">
          <webHttp/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    <protocolMapping>
      <add binding="webHttpBinding" scheme="https"/>
    </protocolMapping>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" multipleSiteBindingsEnabled="true"/>
  </system.serviceModel>
</configuration> 
```

