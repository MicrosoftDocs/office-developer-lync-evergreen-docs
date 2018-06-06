---
title: Debugging Lync SDN Manager
TOCTitle: Debugging Lync SDN Manager
ms:assetid: 5567fd7c-4567-47c4-8aa2-456564fcd087
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785215(v=office.15)
ms:contentKeyID: 62952699
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Debugging Lync SDN Manager


_**Applies to:** Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013_

**In this article**  
Activating WCF service logging  
Activating the message receiver log service  
Validating LDL’s Client Certificate in LSM  
Replaying logs  

The Lync SDN Interface 2.1.1 provides several advanced features to improve security and to help you debug configuration issues.

## Activating WCF service logging

The LSM supports advanced debugging via WCF. Instead of detailing how to use or change this, we provide an example as an illustration as follows. For complete information on this subject, see the WCF documentation. By uncommenting and customizing the section that follows, which is an excerpt from an SDNManager.exe.config file, you can receive low level debugging logs from the WCF service.

``` xml
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
```

## Activating the message receiver log service

The LSM contains a simple REST WebService which can receive messages and log them for later analysis. This build-in service can be used to simulate a Lync SDN-aware network controller.

To start this service, you need to uncomment the following section in the SDNManager.exe.config file. When uncommented and customized, it will start a service, using both HTTP and HTTPS, to receive random xml messages and to log them to the "LogOutput.log" log file (RelayData – log cannel).

``` 
      <service name="Microsoft.Rtc.Enlightenment.Hub.LogService">
        <endpoint address="http://localhost:9333/Log" behaviorConfiguration="webby" bindingConfiguration="wsHttpEndpointBindingNoSec"
          binding="webHttpBinding" name="ep1" contract="Microsoft.Rtc.Enlightenment.Hub.ILogService" />
        <endpoint address="https://localhost:9332/Log" behaviorConfiguration="webby" 
          binding="webHttpBinding" bindingConfiguration="wsHttpEndpointBindingNoCert"
          name="ep1" contract="Microsoft.Rtc.Enlightenment.Hub.ILogService">
          <identity>
            <dns value="ServerSideCert" />
          </identity>
        </endpoint>
      </service>
```

You can configure the LSM setting to use the log service by changing the submitUri value to "http://localhost:9333/Log/PostStuffHere", instead of an actual network controller’s web service address.


> [!NOTE]
> <P>You can also view the last megabyte of messages received by browsing to http://localhost:9333/Log/GetStuffHere.</P>



## Validating LDL’s Client Certificate in LSM

By default LSM uses a simple custom validator for client certificates received from the LDL. WCF ensures that a certificate is consistent and valid before this validator is called. This validator ("AcceptAndLogValidator") logs information from the certificate and always accepts it.

For an increased security, you must configure a different and appropriate validator for client certificates using standard WCF configuration mechanisms. The following example shows the WCF configuration for the AcceptAndLogValidator:

``` 
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
```

## Replaying logs

As another debugging feature, LSM allows for replaying recorded input logs. The LSM can log all messages it receives from the LDLs. By using the SDNManager command line tool, you can send such a log to the LSM service and have it executed. Furthermore, the logs can be replayed with or without the original timing.

1.  Activate logging AllInputLog Listener in the SDNManager.exe.config file (see [Configuring LDL logging options](configuring-ldl-logging-options.md)). Only the logs generated by the LSM can be replayed from this Listener.

2.  Use the SDNManager.exe with the **/e** or **/et** parameters to replay the log file.

3.  Use the LyncDialogListener.exe either the **/e** or **/et** parameters to replay recorded sip log files either recorded by the LDL or from Lync Server itself.

