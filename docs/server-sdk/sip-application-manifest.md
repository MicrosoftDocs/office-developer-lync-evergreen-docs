---
title: SIP application manifest
TOCTitle: SIP application manifest
ms:assetid: 3a5d8ad8-08c2-4dee-b39c-b19860ca23c6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439064(v=office.15)
ms:contentKeyID: 57096220
ms.date: 02/11/2016
mtps_version: v=office.15
dev_langs:
- xml
---

# SIP application manifest

The SIP application manifest is an XML document that describes a SIP application to the Microsoft Lync Server 2013 instance against which the application runs.


**Applies to**: Lync Server 2013

The following workflow is controlled by the application manifest:

  - Specifies the location of your application and its namespace information.

  - Specifies the kinds of SIP messages on which your application performs routing and filtering processes.

  - Contains the script that performs the actual message processing or dispatches the message to a managed code component.

The manifest contains a set of child elements that define key properties of the application, including the kinds of SIP messages to filter and whether the application is a script-only application. The child elements are used to specify a logic that is used to dispatch specific kinds of SIP messages to the application and to filter other kinds of SIP messages.

For a script-only SIP application, the application manifest document is loaded to the server when the application registers with Lync Server 2013. For a managed SIP application, the manifest is loaded to the server, through the Microsoft.Rtc.Sip.ServerAgent managed class, when the application starts.

## SIP application manifest example

The following application manifest handles SIP INVITE and MESSAGE requests.

```xml
<?xml version="1.0" ?>

<!-- Set the application URI, the namespace prefix, and the namespace name -->
<lc:applicationManifest
    appUri="http://www.adatum.com/myApplicationLocation"
    xmlns:lc="http://schemas.microsoft.com/lcs/2006/05">

    <!-- Define properties of the application -->
    <lc:requestFilter methodNames="INVITE,MESSAGE"
                      strictRoute="false"
                      registrarGenerated="true"
                      domainSupported="true"/ >
    <lc:responseFilter reasonCodes="NONE" />
    <lc:proxyByDefault action="true" />
    <lc:scriptOnly />

    <!-- The message filtering script -->
    <lc:splScript><![CDATA[
      if (sipRequest) {
        if (sipRequest.Method == StandardMethod.Invite) {
          Dispatch("NameOfInviteHandlerMethodInApplicationHere");
        }
        else if (sipRequest.Method == StandardMethod.Message) {
          Dispatch("NameofMessageHandlerMethodInApplicationHere");
        }
      }
    ]]></lc:splScript>

</lc:applicationManifest>
```

In this example, the **appUri** attribute of the **applicationManifest** element specifies the URI that uniquely identifies the application to Lync Server 2013. The **xmlns** attribute specifies the namespace alias. The namespace alias identifies the XML elements in the manifest that are specific to the application. In this example, the namespace alias is set to lc and is separated from each element name with a colon.

The **requestFilter** element sets the basic filters for SIP requests, and the **responseFilter** element sets the basic filters for response messages. These settings control the kinds of messages that the application processes. In the previous example, only requests with a SIP method kind of INVITE or MESSAGE are dispatched to the application. SIP reason codes from responses are not passed to the application.

The presence of the **scriptOnly** element indicates that the application has no managed code component and that all message handling is performed completely within the Microsoft SIP Processing Language (MSPL) script. For SIP managed code applications, this element must be absent from the manifest.

The message filtering script is defined in the CDATA section that is contained in the **splScript** element.

If the application is registered with Lync Server 2013 to run at a priority higher than the UserServices application that is installed by default as part of the server deployment, the \<allowRegistrationBeforeUserServices/\> element must be specified.

For information about descriptions of other application manifest elements, see [Application Attribute Elements](https://msdn.microsoft.com/en-us/library/dd185854\(v=office.15\)).

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

