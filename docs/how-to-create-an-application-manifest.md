---
title: 'How to: Create an application manifest'
TOCTitle: 'How to: Create an application manifest'
ms:assetid: ad200e17-2e8f-44b7-933f-7f0445462acf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439077(v=office.15)
ms:contentKeyID: 57096671
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# How to: Create an application manifest

Learn how to create an application manifest that runs on Microsoft Lync Server 2013.


_**Applies to:** Lync Server 2013_

To create a SIP application that runs on Lync Server 2013, the first step is to create an application manifest. The application manifest contains both the basic rules for message delivery to the application and the Microsoft SIP Processing Language (MSPL) script that is used to process the message.

## Design options: MSPL script or .NET Framework-based managed SIP application

You can create two kinds of SIP applications with the Microsoft Lync Server 2013 SIP Application API:

  - MSPL script-only SIP applications that are embedded in the application manifest

  - .NET Framework-based managed SIP applications

MSPL script-only applications are appropriate for the following scenarios:

  - Proxying SIP messages of a specific type

  - Handling potentially complex branching proxy scenarios or supporting multiple points-of-presence (MPOP), where extensibility is not required
    

    > [!NOTE]
    > <P>For information about the descriptions of the functionality that MSPL supports, see <A href="https://msdn.microsoft.com/en-us/library/hh364711(v=office.15)">Microsoft SIP Processing Language Reference</A>.</P>



Managed SIP applications are appropriate for the following scenarios:

  - Handling potentially complex branching proxy scenarios or supporting MPOP, where extensibility is required

  - Working directly with SIP transaction objects and supporting multiple work threads
    

    > [!NOTE]
    > <P>If you build a managed SIP application, you must also determine the division of labor between the message filter (the script block that dispatches specified messages) and the application (the managed code event handler that processes the dispatched messages).</P>



## Application manifest template

After deciding the kind of application that you need, use an XML or text editor to write the content of the application manifest by using the following template:

``` xml
<?xml version="1.0" ?>
<lc:applicationManifest
 lc:appUri="URI"
 xmlns:lc=http://schemas.microsoft.com/lcs/2006/05>
 
  <!-- remove the following element for managed SIP app -->
  <lc:script-only />   
    
  <!-- required if the app’s priority is higher than that of UserServices -->
  <lc:allowRegistrationBeforeUserServices/> 
 
  <lc:proxyByDefault action="true|false"/>
  <lc:requestFilter methodName="…", … />
  <lc:responseFilter reasonCodes= "…" />

  <lc:splScript>
    <![CDATA[

    insert_message_filter_script_here

    ]]>
  </lc:splScript>
</lc:applicationManifest>
```


> [!NOTE]
> <P>The <STRONG>&lt;script-only&gt;</STRONG> element must be the last child element of the <STRONG>&lt;applicationManifest&gt;</STRONG> element.</P>



The appUri attribute value can be any HTTP URL that can uniquely identify the SIP application to the Lync Server 2013 instance.

### Saving the application manifest

For MSPL script applications, save the manifest as a text file with an .am extension.

For managed SIP applications, either save the manifest as a text file with the .am extension or embed it in an application assembly as a resource. Application manifests can also be generated in-line or dynamically. For example, an application can filter on location-specific URIs or domain values that are supplied by code logic.

## See also

#### Concepts

[SIP application manifest](sip-application-manifest.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

#### Other resources

[applicationManifest element](https://msdn.microsoft.com/en-us/library/hh364639\(v=office.15\))

[splScript element](https://msdn.microsoft.com/en-us/library/hh364698\(v=office.15\))

