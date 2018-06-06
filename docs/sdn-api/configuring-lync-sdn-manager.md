---
title: Configuring Lync SDN Manager
TOCTitle: Configuring Lync SDN Manager
ms:assetid: 2a85a4b0-3bcc-4d91-a46a-a39e48d7a35a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775151(v=office.15)
ms:contentKeyID: 62626125
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Configuring Lync SDN Manager


_**Applies to:** Lync 2013_

**In this article**  
Configuring Lync SDN Manager logging options  
Configuring Lync SDN Manager execution options  
Web service configuration  
Advanced configuration for debugging and logging  

**Note**: The steps presented in this section are optional unless you want to modify the default configurations.

The Lync SDN Manager (LSM) logging can be configured by editing the SDNManager.exe.config file located in the default installation directory. The process is similar to configuring LDL logging.

## Configuring Lync SDN Manager logging options

You can configure the logging options for the LSM by following the same steps for the LDL. Please see [Configuring Lync Dialog Listener](configuring-lync-dialog-listener.md) for more information.

## Configuring Lync SDN Manager execution options

Follow the steps below to modify the Lync SDN Manager (LSM) execution configuration.

### Configure LSM execution options

1.  Navigate to the API installation directory.

2.  Open the SDNManager.exe.config file with a text editor.

3.  Search for the \<appSettings\> section and make appropriate changes to relevant entries therein.

The configuration for executing the LSM service is flexible. The following table shows a few options, as an illustration.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Defaultconfiguration</strong></p></td>
<td><p><strong>Description</strong></p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;submituri&quot; value=&quot;http://YourSdnController&quot; /&gt;</p></td>
<td><p>Set the value of the web address for the controller. This is populated by the installer but can be updated through this configuration. This can be one or more values, separated by comma, semicolon, or space.</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;backwardcompatibility&quot; value=&quot;false&quot; /&gt;</p></td>
<td><p>Set the value of the backward compatibility mode. If this value is set to true, then the LSM will forward the version 1.0 schema format.</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;clientcertificateid&quot; value=&quot;&quot; /&gt;</p></td>
<td><p>When using SSL, LSM will use this thumbprint to locate a client certificate in the local store to use for connecting to the network controllers</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;submitqueuelen&quot; value=&quot;100&quot; /&gt;</p></td>
<td><p>Set value to the maximum unanswered and waiting messages to send to each recipient. Change this value only if network conditions require a longer queue length due to delays in messages being received by the network management system.</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;calltimeout&quot; value=&quot;6:00:00&quot; /&gt; &lt;!-- 6 hours --&gt;</p></td>
<td><p>Maximum time expected for a call, after which state kept will be dropped.</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;invitetimeout&quot; value=&quot;0:02:00&quot; /&gt; &lt;!-- 2 min --&gt;</p></td>
<td><p>Maximum time expected for ringing, before either an error is sent or the user picked up</p></td>
</tr>
<tr class="even">
<td><p>&lt;add key=&quot;qoetimeout&quot; value=&quot;0:00:05&quot; /&gt; &lt;!-- 5 secs --&gt;</p></td>
<td><p>Time to wait after the last QoE report before forwarding a merged report to the network controller(s)</p></td>
</tr>
<tr class="odd">
<td><p>&lt;add key=&quot;endedtimeout&quot; value=&quot;0:01:00&quot; /&gt; &lt;!-- 1 min --&gt;</p></td>
<td><p>Time to wait after the Ended message before cleaning up the call if no QoE report is received.</p></td>
</tr>
</tbody>
</table>


## Web service configuration

By default, the submituri value for the Web service is set to http://localhost:9333/LDL and https://localhost:9332/LDL. For https, the manager expects a valid certificate for both client and server certificates.

## Advanced configuration for debugging and logging

The LSM supports advanced debugging via a WCF service. By uncommenting and customizing the section below, you can send low level debug messages to a WCF service.

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

You can also turn on some additional logging by uncommenting the section below. When uncommented and customized, it will start a service, with both options for http and https, to receive "random" xml messages and log them to the "OutputData" logging channel.

          <!--<service name="Microsoft.Rtc.Enlightenment.Hub.LogService">
            <endpoint address="http://localhost:9333/Log"
              binding="webHttpBinding" behaviorConfiguration="webby"
              name="ep1" contract="Microsoft.Rtc.Enlightenment.Hub.ILogService" />
            <endpoint address="https://localhost:9332/Log"
              binding="webHttpBinding" bindingConfiguration="wsHttpEndpointBindingNoCert"
              behaviorConfiguration="webby"
              name="ep1" contract="Microsoft.Rtc.Enlightenment.Hub.ILogService" >
              <identity>
                <dns value="ServerSideCert"/>
              </identity>
            </endpoint>
          </service>-->

The WCF configuration allows for testing and running the Lync SDN API without needing a network controller that accepts the Lync SDN API message format. You can configure this setting by changing the submitUri value to "http://localhost:9333/Log/PostStuffHere", instead of a network controller’s web service.


> [!NOTE]
> <P>You can view the last megabyte of messages received by browsing to http://localhost:9333/Log/GetStuffHere.</P>


