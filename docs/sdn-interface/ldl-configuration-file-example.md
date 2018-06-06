---
title: LDL configuration file example
TOCTitle: LDL configuration file example
ms:assetid: 6c325272-f444-4b8e-a9ac-80ebec5e2bff
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785226(v=office.15)
ms:contentKeyID: 62952709
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# LDL configuration file example


_**Applies to:** Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013_

The following code sample is n example of the LDL configuration file.

## A sample of LyncDialogListener.exe.config file

``` xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" requirePermission="true" />
  </configSections>
 
  <loggingConfiguration name="" tracingEnabled="true" defaultCategory="Error">
    <listeners>
      <add name="LNEAppLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        fileName="%TEMP%\LNEApp.log" footer="" formatter="LNEDetailFormatter"
        header="" rollFileExistsBehavior="Increment" rollInterval="Day"
        rollSizeKB="10000" traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
      <add name="AllDataLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        fileName="%TEMP%\AllData.log" footer="" formatter="SimpleOutput"
        header="" rollFileExistsBehavior="Increment" rollInterval="Day"
        rollSizeKB="10000" />
      <add name="QoEInputDataLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        fileName="%TEMP%\QoEInputData.log" footer="" formatter="SimpleOutput"
        header="" rollFileExistsBehavior="Increment" rollInterval="Day"
        rollSizeKB="10000" />
      <add name="DialogDataLog" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        fileName="%TEMP%\DialogData.log" footer="" formatter="SimpleOutput"
        header="" rollFileExistsBehavior="Increment" rollInterval="Day"
        rollSizeKB="10000" />
    </listeners>
    <formatters>
      <add type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        template="{timestamp(local:O)}{tab}{message}{tab}{dictionary({tab}{key}: {value})}"
        name="LNEOverviewFormatter" />
      <add type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        template="{timestamp(local:O)}{tab}[{category}]{tab}{message}{tab}{dictionary({tab}{key}: {value})}"
        name="LNEDetailFormatter" />
      <add type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=5.0.414.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
        template="{message}{newline}" name="SimpleOutput" />
    </formatters>
    <categorySources>
      <add switchValue="Off" name="Debug">
        <listeners>
          <add name="LNEAppLog" />
        </listeners>
      </add>
      <add switchValue="All" name="Error">
        <listeners>
          <add name="LNEAppLog" />
        </listeners>
      </add>
      <add switchValue="Off" name="QoEInputData">
        <listeners>
          <add name="QoEInputDataLog" />
          <add name="AllDataLog" />
        </listeners>
      </add>
      <add switchValue="Off" name="DialogData">
        <listeners>
          <add name="AllDataLog" />
          <add name="DialogDataLog" />
        </listeners>
      </add>
      <add switchValue="All" name="Info">
        <listeners>
          <add name="LNEAppLog" />
        </listeners>
      </add>
      <add switchValue="All" name="TransmissionError">
        <listeners>
          <add name="LNEAppLog" />
        </listeners>
      </add>
    </categorySources>
    <specialSources>
      <allEvents switchValue="All" name="All Events" />
      <notProcessed switchValue="ActivityTracing" name="Unprocessed Category">
        <listeners>
          <add name="LNEAppLog" />
        </listeners>
      </notProcessed>
      <errors switchValue="All" name="Logging Errors &amp; Warnings">
        <listeners>
          <add name="LNEAppLog" />
        </listeners>
      </errors>
    </specialSources>
  </loggingConfiguration>
  <appSettings>
    <add key="submituri" value="http://localhost:9333/LDL" />  <!-- URI to locate the LSM (used unless checkdns is true) -->
    <add key="alternativeuri" value="" />  <!-- secondary URI to locate an LSM, in case the primary is unavailable in a Active/Standby configuration -->
    <add key="clientcertificateid" value="" /> <!-- thumbprint of a client certificate to use to authenticate the LDL with the LSM -->
    <add key="checkdns" value="false" />  <!-- use a URI provided by the DNS SRV record for locating a pool of LSMs -->
  </appSettings>
</configuration>
```

