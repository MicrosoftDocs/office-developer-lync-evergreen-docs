---
title: 'How to: Configure garbage collection on the server'
TOCTitle: 'How to: Configure garbage collection on the server'
ms:assetid: 522d932d-6f76-4184-a67e-116ee0a83b69
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439085(v=office.15)
ms:contentKeyID: 57096242
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Configure garbage collection on the server

Learn how to configure garbage collection in a Microsoft Lync Server 2013 deployment.


**Applies to**: Lync Server 2013

## Configuring garbage collection on the server

You can use the server-optimized garbage collector (GC), instead of the default workstation GC, to improve the performance of a Microsoft Lync Server 2013 SIP Application Managed API managed code application.

The workstation GC is the default GC mode and is the only GC that is used on single-processor computers. The workstation GC is hosted in console and Windows Forms applications. It performs full (generation 2) collections concurrently with the running program, with minimal latency. This mode is useful for client applications, where perceived performance is usually more important than raw throughput.

The server GC is available only on multiprocessor computers. It creates a separate managed heap and thread for each processor and performs collections in parallel. During collection, all managed threads are paused (threads running native code are paused only when the native call returns). In this way, the server GC mode maximizes throughput (the number of requests per second) and improves performance as the number of processors increases. Computers with four or more processors offer improved performance. All managed code applications that use the Lync Server 2013 SIP Application Managed API should use the server GC.

Using the Microsoft .NET Framework, you can run server GC in a non-hosted managed application by adding the following element to the application's configuration file.

    <configuration
       <runtime>
          <gcServer enabled="true"/>
       </runtime>
    </configuration>


> [!NOTE]
> <P>When you set the &lt;gcServer/&gt; element to "true", the &lt;gcConcurrent/&gt; element (the default workstation GC identifier) is disabled.</P>



Ensure the configuration file name uses the MyApp.exe.config format and save it in the same directory as MyApp.exe.

## See also

#### Concepts

[Managed SIP Application API](managed-sip-application-api.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

