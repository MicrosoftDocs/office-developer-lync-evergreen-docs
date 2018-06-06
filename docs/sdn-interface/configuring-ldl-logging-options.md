---
title: Configuring LDL logging options
TOCTitle: Configuring LDL logging options
ms:assetid: bd414d81-e05e-41ab-834f-7a97093a628d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785207(v=office.15)
ms:contentKeyID: 62952688
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Configuring LDL logging options


_**Applies to:** Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013_

Lync SDN Interface 2.1.1 uses the logging infrastructure of the [Enterprise Libraries 5.0](http://msdn.microsoft.com/en-us/library/ff632023.aspx). You can inspect and modify the configuration file by using the Microsoft Enterprise Library Configuration Tool. For a complete documentation on the options and capabilities of the logging infrastructure, see [Configuring the Logging Application Block](http://msdn.microsoft.com/en-us/library/ff664569\(v=pandp.50\).aspx) in the Enterprise Libraries documentation.

The Enterprise Libraries includes a configuration tool that provides an intuitive graphical user interface for adding and changing settings for the logging configuration. You can use this tool to configure the LDL logging options. This article explains how to configure the logging options in the LyncDialogListener.exe.config file.

## Configuring LDL logging options

To manually set the most common logging configurations:

  - Navigate to the LDL installation directory.

  - Open the *LyncDialogListener.exe.config* file with a text editor.

  - Search for the \<loggingConfiguration\> section and make appropriate changes to entries under the \<listeners\>, formatters and categorySource elements.
    
    Here, the \<listeners\> element specifies the log output, including the log file location and file rotation policies. They refer to a particular formatter to be used. Each entry, an \<add\> element, under \<listeners\> specifies a type of logging. Modifications can include adding a new \<add\> entry to enable the specified type of logging, removing an \<add\> entry to disable the specified type of logging, and changing an existing \<add\> entry to change the specified type of logging.
    
    The \<formatters\> element specifies the style for each log entry. The \<categorySource\> element specifies bindings of the log channels used in LDL and LSM to particular listeners. The switchValue could be Off or All indicating whether this log channel is active. For a more thorough investigation of issues, you must start the Debug channel by setting the switchValue to All, as shown. \\
    
    ``` xml
          <add switchValue="All" name="Debug">
            <listeners>
              <add name="LNEAppLog" />
            </listeners>
          </add>
    ```

The following example shows the LNEAppLog type of logging options containing a modified logging file path (in the boldface text).

``` xml
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
     rollSizeKB="100000" 
     traceOutputOptions="LogicalOperationStack, 
     DateTime, Timestamp, ProcessId, ThreadId, Callstack"/>
</listeners>
```

The Lync Dialog Listener service default configuration supports the following types of logging.

Lync Dialog Listener logging configuration

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
<td><p>Logging the application execution states, including Info and Error types of data as well as adding activated Debug channel. The output is recorded in the LyncDiagnostics.log file. This file won't contain any PII.</p></td>
</tr>
<tr class="even">
<td><p>AllDataLog</p></td>
<td><p>Logging all input data, including SIP messages with SDP headers, and raw quality of experience reports.</p></td>
</tr>
<tr class="odd">
<td><p>QoEInputDataLog</p></td>
<td><p>Logging the quality of experience raw data from the Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>DialogDataLog</p></td>
<td><p>Logging the dialog data, including SIP messages and SDP headers.</p></td>
</tr>
</tbody>
</table>


The LSM default configuration supports the following types of logging:

Lync SDN Manager logging configuration

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
<td><p>Logging the application execution states, including Info, and Error types of data as well adding Debug, if activated. The output is recorded in the LyncSDNManager.log file. This file won’t contain any PII.</p></td>
</tr>
<tr class="even">
<td><p>AllOutputLog</p></td>
<td><p>Logging all output data sent to Network Controllers. The output is recorded in the AllOutputManager.log file</p></td>
</tr>
<tr class="odd">
<td><p>AllInputLog</p></td>
<td><p>Logging all input data received from LDLs. This data can be replayed and the output is recorded in the AllInputManager.log file.</p></td>
</tr>
<tr class="even">
<td><p>ErrorMsgLog</p></td>
<td><p>Logging individual messages about processing issues and the respective error messages for further investigation. The output is recorded in the ErrorMsgManager.log file.</p></td>
</tr>
<tr class="odd">
<td><p>LogOutputLog</p></td>
<td><p>Logging the messages received at the Message Receiver Log Service. The output is recorded in the LogOutput.log file. For more information, see <a href="debugging-lync-sdn-manager.md">Debugging Lync SDN Manager</a>.</p></td>
</tr>
<tr class="even">
<td><p>QoEInputDataLog</p></td>
<td><p>Logging the quality of experience raw data of the Lync Server received from LDLs. The output is recorded in the QoEInputManager.log file.</p></td>
</tr>
<tr class="odd">
<td><p>QoEDataLog</p></td>
<td><p>Logging the raw QoE reports. The output is recorded in the QoEDataManager.log file.</p></td>
</tr>
<tr class="even">
<td><p>DialogDataLog</p></td>
<td><p>Logging the dialog data, including SIP messages, received from the LDLs. The output is recorded in the DialogData.log file.</p></td>
</tr>
</tbody>
</table>



> [!WARNING]
> <P>The LyncDiagnostics.log as well as the LyncSDNManager.log will not contain person-identifiable information (PII), even in debug-level, while any of the other logs might also contain un-obfuscated user aliases, names and telephone numbers. Activate this logs with caution.</P>



## Additional resources

  - [Configuring Lync SDN Interface 2.1.1 Lync Dialog Listener](configuring-lync-sdn-interface-2-1-1-lync-dialog-listener.md)

  - [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

