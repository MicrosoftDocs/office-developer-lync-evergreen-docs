---
title: Register contextual conversation packages
TOCTitle: Register contextual conversation packages
ms:assetid: 1d9bdbb4-7602-4057-88cb-37b933acc3fc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945539(v=office.15)
ms:contentKeyID: 51541340
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Register contextual conversation packages

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the concept of Conversation Window Extension registration using Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Understanding Install and Runtime Registration<br />
Register the contextual conversation package<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Contextual conversation packages

A contextual conversation registration package registers an application with the local system registry so that the identity of the application can be validated before the application can send or receive contextual data in a conversation. A registration package can set up to eight registry key values, depending on the type of contextual application to be registered. A contextual application can be one of the following types:

  - **Conversation window extension application**.
    
    This is a Silverlight browser application that access contextual data through a hosting conversation. **ExtensibilityWindowSize**, **InternalURL**, **ExternalURL**, and **InstallLink** values should be set.

  - **Lync 2013 Conversation-specific WPF or Windows forms desktop application**.
    
    This is an application that is started by Lync 2013when a new conversation with the appropriate context is opened. The instance of this application that is started should get only the conversation context of the associated conversation. This type of application requires that its contextual conversation registration includes a **Path** to the executable to be started.

  - **User-started WPF window, Windows forms desktop application, or service**.
    
    This application is not started by the Microsoft Lync 2013 client. Instead, the application is started by another agent such as the local user. The application uses the Lync 2013 API to start or accept new conversations and then sends and receives contextual data. This type of application requires that the **Name** value is set in its contextual package. An example of this type of application is a custom client that runs in a UI suppression scenario and replaces the suppressed UI of Lync 2013.
    
    The **Path**, **InternalURL**, and **ExternalURL** values must not be set. If any of these values are set, Lync 2013 starts a new instance of the application for any conversation conveying context whose application Id matches the subkey GUID of the registration package.

## Understanding Install and Runtime Registration

Contextual software installation is designed to be flexible and support security for enterprises, independent software vendors, and system integrators.

There are two ways to register a contextual application:

  - Install Registration

  - Runtime Registration

These two choices are compatible. In fact, the recommended practice is to perform Install Registration to install the contextual application, and then Runtime Registration every time that the application starts.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Runtime Registration provides extra security around the GUID used in registration. The GUID can only be used in the same thread where Runtime Registration is used. If another thread tries to use that GUID to identify the contextual application, access the contextual context, or open Microsoft Lync 2013 CWE, an access denied exception is thrown. To use the GUID in more than one thread, use Install Registration. In this case, consider that your contextual data can be accessed by other applications running on the same computer as long as they have access to the Lync 2013 API.</p></td>
</tr>
</tbody>
</table>

### Install Registration

Install Registration uses a setup application or Group Policy to position entries into the registry. In this case, package registration data persists after Lync 2013 signs out or exits. Use Install Registration for better control of package setup. For more information, see [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md).

Install Registration is a good choice for scenarios such as the following:

Anytime a sales manager gets a call from an outside customer, she wants to see, by default, her Customer Relationship Management (CRM) record for that person. However, the particular view of that application that she sees is based on her role and the administrator has set up pools of Group Policy object (GPO) settings to ensure different roles see different views of the CRM application.

### Runtime Registration

In contrast with Install Registration, Runtime Registration uses an application to modify package registration data at runtime. Use Runtime Registration for flexible package setup and the security advantages. In this case, package registration data is added to the Lync 2013 registration pool and resets after the Lync 2013 user signs out. Use the [ApplicationRegistration](https://msdn.microsoft.com/en-us/library/jj293820\(v=office.15\)) class to perform Runtime Registration. For more information, see [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md).

Runtime Registration is a good choice for scenarios such as the following:

An application only wants to provide a contextual experience when it is running. For example, Sam is a financial advisor who uses Lync 2013 to talk with his clients. When his market tracking software is open and he gets a call from a customer, it changes the application view to show the customer’s portfolio. This call is automatically noted in the finance software for auditing reasons. Because of auditing requirements, a customized view is not available unless the finance software is running.

### Interaction between Runtime and Install Registration

Runtime Registration does not configure Microsoft Windows registry entries. Instead, it creates a new application package that exists in the Lync 2013 registration pool until the current Lync 2013 user signs out. Runtime Registration can exist without Install Registration, but if you use Runtime Registration consider using Install Registration as well. In a case where Runtime Registration and Install Registration occur with the same application ID, Runtime Registration overrides Install Registration during the life of the session. When the user signs out, Runtime Registration resets and Install Registration starts.

### Conversation package location restrictions

Contextual conversation packages can be installed to a UNC, URL, or file path. To simplify management of the package, install it to a URL or UNC.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>By default, contextual links in the form of UNC paths are not trusted. The untrusted UNC path must be added to the list of Trusted Sites maintained by Microsoft Internet Explorer to start the contextual application in CWE. Internal URLs resolving to Localhost, computer name, local loopback address, or actual IP address must be added to Trusted Sites.</p></td>
</tr>
</tbody>
</table>

The following table summarizes the security status of contextual conversation packages installed on specified UNC paths.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Location</p></th>
<th><p>Permission</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Local file</p></td>
<td><p>Allowed</p></td>
</tr>
<tr class="even">
<td><p>Network share</p></td>
<td><p>Blocked</p></td>
</tr>
<tr class="odd">
<td><p>Network share in Trusted Site</p></td>
<td><p>Allowed</p></td>
</tr>
<tr class="even">
<td><p>Network drive</p></td>
<td><p>Blocked</p></td>
</tr>
<tr class="odd">
<td><p>Network drive with computer name on Trusted Site</p></td>
<td><p>Allowed</p></td>
</tr>
<tr class="even">
<td><p>Virtual drive pointing to local drive</p></td>
<td><p>Allowed</p></td>
</tr>
<tr class="odd">
<td><p>Local drive from Visual Studio</p></td>
<td><p>Allowed</p></td>
</tr>
<tr class="even">
<td><p>Network drive pointing to local computer share</p></td>
<td><p>Blocked</p></td>
</tr>
</tbody>
</table>

## Register the contextual conversation package

Specify a default application to provide a context when none is available. For example, when a sales manager gets a call, a CRM application automatically starts and displays key information about the caller. For more information, see [Understand the role of the default CWE application registration package](understand-the-role-of-the-default-cwe-application-registration-package.md).

Specify rich context handling and applications. For example, when two oil field engineers consult about a field, the company’s line-of-business application automatically starts to run and it provides various graphical displays that represent geological data. For more information, see [Consume data and handle events in a contextual conversation](consume-data-and-handle-events-in-a-contextual-conversation.md).

### To register a context package

1.  Install the context application.

2.  Add registry keys as appropriate.

3.  Perform steps 1 and 2 on both the sending and receiving computers.

**Registration data values**

Add the context application GUID as a key under this path:

  - **HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\\Addins**

For more information about application GUIDs, see [Create GUID (guidgen.exe)](http://go.microsoft.com/fwlink/?linkid=192728%26clcid=0x409).

The following table lists the case-sensitive values to add to this key.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Value name</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>REG_SZ</p></td>
<td><p>Required. The name of the context application. For example, &quot;Blue Yonder Airlines.&quot;</p></td>
</tr>
<tr class="even">
<td><p>InstallLink</p></td>
<td><p>REG_SZ</p></td>
<td><p>Optional. Specifies a URL pointing to an installation file that you provide. A clickable link displays if a package is not installed on the receiving computer.</p></td>
</tr>
<tr class="odd">
<td><p>DefaultContextPackage</p></td>
<td><p>REG_DWORD</p></td>
<td><p>Optional, defaults to 0. Specifies whether this package is the default package for all unassigned calls. 0 = false, 1 = true.</p></td>
</tr>
<tr class="even">
<td><p>ExtensibilityWindowSize</p></td>
<td><p>REG_DWORD</p></td>
<td><p>Optional, defaults to 0. Sets the minimum size of CWE. 0 = small (300 x 200 pixels), 1 = medium (400 x 600 pixels), 2 = large (800 x 600 pixels).</p></td>
</tr>
<tr class="odd">
<td><p>InternalURL</p></td>
<td><p>REG_SZ</p></td>
<td><p>Required only for applications running inside CWE. Specifies a context application URL in the Lync Server 2013 domain. The application automatically detects which URL to use, InternalURL or ExternalURL, based on the client location. This entry also accepts the three optional parameters described in the following table.</p></td>
</tr>
<tr class="even">
<td><p>ExternalURL</p></td>
<td><p>REG_SZ</p></td>
<td><p>Optional. Specifies a context application URL located outside the Lync Server 2013 domain and is required when a client signs in from outside that domain. The application automatically detects which URL to use, InternalURL or ExternalURL, based on the client location. This entry also accepts the three optional parameters described in the following table.</p></td>
</tr>
<tr class="odd">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p>Optional. Specifies the path of a desktop application and determines whether the start link appears. If not present, the start link does not appear.</p></td>
</tr>
<tr class="even">
<td><p>Parameters</p></td>
<td><p>REG_SZ</p></td>
<td><p>Optional. Specifies one or more parameters for the Path value. This entry also accepts the three optional parameters described in the following table.</p></td>
</tr>
</tbody>
</table>

The following table describes the three optional parameters for the Parameters value, as mentioned in the previous table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>%AppData%</p></td>
<td><p>Use this parameter to obtain the application data sent in a contextual conversation. The value is the same as the value of the <strong>ConversationContextualInfo.ApplicationData</strong> property. The size limit is 2 KB.</p></td>
</tr>
<tr class="even">
<td><p>%AppId%</p></td>
<td><p>Use this parameter to obtain the application GUID sent in a contextual conversation. The value is the is the same as the value of the <strong>ConversationContextualInfo.ApplicationId</strong> property. The size limit is 38 characters, which is the size of an application GUID.</p></td>
</tr>
<tr class="odd">
<td><p>%AppName%</p></td>
<td><p>Use this parameter to obtain the application name sent in a contextual conversation. The value is the same as the Name value in the Windows Registry. The size limit is 50 characters.</p></td>
</tr>
</tbody>
</table>

**Sample registry entries**

    HKEY_CURRENT_USER\Software\Microsoft\Communicator\ContextPackages\{55058F71-6ACF-48D0-B20E-BC7668695371}]
    "DefaultContextPackage"=dword:00000000
    "Path" ="http://localhost/Test/sample2.html""Name"="Blue Yonder Airlines"
    "ExtensibilityWindowSize"=dword:00000001
    "Parameters"="%AppData%,%AppId%"

## See also

  - [Contextual Lync conversations](contextual-lync-conversations.md)

  - [How to: Start an extension application in a Lync conversation window](how-to-start-an-extension-application-in-a-lync-conversation-window.md)

