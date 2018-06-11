---
title: Get started with Lync 2013 SDK
TOCTitle: Get started
ms:assetid: e7cd673b-c786-4dbe-a6b4-940ffef372fd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933215(v=office.15)
ms:contentKeyID: 50877361
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Get started with Lync 2013 SDK

Learn about getting started using Microsoft Lync 2013 SDK, the essential features of the SDK, and how you can use those features to give your application enhanced unified communication features that are supported by Microsoft Lync Server 2013.



**Applies to**: Lync 2013 | Lync Server 2013



<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="get-started-with-lync-2013-sdk.md" class="uri"><img src="images/JJ933215.mod_icon_getstartbox(Office.15).gif"/></a>   <a href="get-started-with-lync-2013-sdk.md" class="uri"><img src="images/JJ933215.mod_icon_dobox(Office.15).gif"/></a>   <a href="get-started-with-lync-2013-sdk.md" class="uri"><img src="images/JJ933215.mod_icon_startbox(Office.15).gif"/></a></p></td>
</tr>
</tbody>
</table>

## What is Microsoft Lync 2013 SDK?

Microsoft Lync 2013 SDK includes a comprehensive managed API, documentation, and a set of sample applications that show how to build unified communication features into your application. The API includes classes that represent the Lync client platform, contacts, conversations, online meetings, and conversation modalities. Modalities manage the actual modes of communication within a conversation or meeting. Use the API to sign a user in to Lync, show lists of Lync contacts, or start conversations. Within a conversation, you programmatically interact in conversations by managing conversation modalities.

The Lync platform components of the API are used to sign a user in and out of Lync 2013, maintain the settings and properties of the local user, and publish the user’s availability and notes (personal and OOF). The platform also lets you automate Microsoft Lync 2013 to the extent that you can programmatically open a new conversation window, start an online meeting, or add a contact to the user’s contact list.

## Get started with Microsoft Lync 2013 SDK

The supported development environment for creating applications with Microsoft Lync 2013 SDK is described in this section.

### Supported operating system software

  - Microsoft Windows Server 2008 R2

  - Microsoft Windows 7 (64-bit)

  - Microsoft Windows 7 (32-bit)

Typical current hardware configurations with a minimum of 2 GB of RAM are recommended for the supported operating systems.

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
<td><p>In the Microsoft Visual Studio development system, select <strong>Any CPU</strong> as your custom application build platform target to ensure your application runs on 32-bit and 64-bit operating systems. The default installation path for Lync SDK is the <em>%root%</em>\Program Files (x86) folder.</p></td>
</tr>
</tbody>
</table>

### Application development

To develop Lync SDK applications, the following requirements must be fulfilled:

  - Microsoft Windows Forms or Microsoft Windows Presentation Foundation (WPF) development: Microsoft Visual Studio 2010 SP1 or Visual Studio 2012.

  - Microsoft Silverlight development: Visual Studio 2010 SP1 or Visual Studio 2012.

  - Microsoft .NET Framework 4.0.

  - Silverlight 4.0 runtime, installed with Microsoft Lync 2013.

  - [Microsoft Silverlight 4 Tools for Visual Studio 2010](http://go.microsoft.com/fwlink/?linkid=201842)

Only Microsoft Internet Explorer 7 and later versions support Lync 2013 Silverlight controls.

### Custom application deployment

To deploy a Lync SDK application, application users must be able to sign in to Lync 2013 and the following components must appear on the target computer:

  - Lync SDK redistributable components:
    
      - Microsoft.Office.uc.dll
    
      - Microsoft.Lync.Model.dll desktop version
    
      - Microsoft.Lync.Model.dll Silverlight version

  - Lync 2013

  - Microsoft .NET Framework 4.0

### Microsoft Lync 2013 SDK essentials

Although an inexperienced programmer who understands basic .NET coding concepts can be successful programming with Microsoft Lync 2013 SDK, more robust and scalable applications can be developed if you are familiar with the following programming concepts.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concept</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="event-driven-code-in-lync-sdk.md">Event-driven code in Lync SDK</a></p></td>
<td><p>Learn about event-based programming in Lync SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="asynchronous-programming-in-lync-sdk.md">Asynchronous programming in Lync SDK</a></p></td>
<td><p>Learn about the <strong>System.AsyncCallback</strong> method in Lync SDK.</p></td>
</tr>
<tr class="odd">
<td><p><a href="migrate-an-application-to-lync-2013-sdk.md">Migrate an application to Lync 2013 SDK</a></p></td>
<td><p>Learn how to migrate an existing application to Lync SDK from previous SDK versions.</p></td>
</tr>
<tr class="even">
<td><p><a href="run-an-application-in-multiple-lync-versions.md">Run an application in multiple Lync versions</a></p></td>
<td><p>Learn how to run a Microsoft Lync 2013 API-enabled application on a computer where multiple versions of the Lync client are installed.</p></td>
</tr>
</tbody>
</table>

## What can you do with Microsoft Lync 2013 SDK?

Microsoft Lync 2013 SDK gives you the ability to add a wide range of Lync features to your Windows Forms, WPF, or Silverlight application. These features can be as simple as dropping a presence gumdrop onto an existing Silverlight application for showing the current presence of a user to complex tasks such as creating a full-featured Lync client as a stand-alone application or hosted within your application.

If you want to add a set of Lync features to your WPF or Silverlight application and do not have the time to learn about the Lync 2013 API object model, you can use the suite of Microsoft Lync 2013 Controls to populate contact list and conversation features in your application. To do this, leverage your knowledge of XAML syntax and C\# to set control properties at either design or runtime. The Lync Controls requires that Microsoft Lync 2013 is installed and running on each computer that runs your application.

You can also automate the starting of Lync 2013 conversations and docking Lync conversation windows within your application by using a few simple method calls from the [Microsoft.Lync.Model.Extensibility](https://msdn.microsoft.com/en-us/library/jj278382\(v=office.15\)) namespace. If you use this method to automate conversations, all you need is the SIP address of a Lync user to start a conversation, a container control in your application that hosts the docked conversation window, and a small amount of C\# code to manage docking the conversation window.

If you want to extend the functionality of the Lync conversation window, you can use the full power of the Lync 2013 API object model to create conversation context-aware Silverlight applications that are hosted in an extension pane of the conversation window itself. The object model gives you read-write access to conversation modalities as well as the conversation participant list. Although the Conversation Window Extension (CWE) application is a Silverlight browser application, it has the practical complexity limitations that any browser application has when hosted in a Browser control on a form.

Other tasks that you can do with Microsoft Lync 2013 SDK include:

  - Extending a Persistent Chat window by creating and hosting a Silverlight browser add-in in the chat window.

  - Building a meeting management console application that controls a Lync 2013 meeting window sharing stage and meeting participant list.

  - Building a public-facing conversation client in a building lobby kiosk that is branded with your company logo and locks new conversations down to the modalities that you set and limits conversations to a predefined set of participants.

The following table lists basic tasks that are the building blocks of the previously discussed features.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Task</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj937241(v=office.15)">How to: Sign in to and out of Lync</a></p></td>
<td><p>Shows how to code the sign in/sign out process using the Lync 2013 API in both UI-suppressed and non UI-suppressed scenarios.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-add-logging-to-a-lync-controls-application.md">How to: Add logging to a Lync Controls application</a></p></td>
<td><p>Shows how to add event logging to your Lync Controls-based application.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-use-log-data-to-debug-a-lync-controls-applications.md">How to: Use log data to debug a Lync Controls applications</a></p></td>
<td><p>Shows two basic scenarios where Lync Controls-based applications generate error log entries.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-started-with-lync-controls.md">Get started with Lync Controls</a></p></td>
<td><p>Gets you started using Microsoft Lync 2013 Controls in a WPF or Silverlight browser application.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-started-with-enhanced-presence-in-lync-sdk.md">Get started with enhanced presence in Lync SDK</a></p></td>
<td><p>Gets you started publishing the local user’s presence by using the Lync 2013 API and Lync Controls.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-started-with-lync-contact-lists.md">Get started with Lync contact lists</a></p></td>
<td><p>Gets you started displaying Lync contacts and groups in your application by using the Lync 2013 API or Lync Controls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-started-with-lync-conversations.md">Get started with Lync conversations</a></p></td>
<td><p>Gets you started creating and managing Lync 2013 by using the Lync 2013 API or Lync Controls.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-started-with-lync-meetings.md">Get started with Lync meetings</a></p></td>
<td><p>Builds on Lync 2013 API conversation concepts and shows how to manage conversations as online meetings by using the Lync 2013 API.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-started-with-persistent-chat.md">Get started with Persistent Chat</a></p></td>
<td><p>Gets you started creating add-in applications for Lync 2013 Persistent Chat room windows.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-started-with-desktop-application-and-display-sharing.md">Get started with desktop, application, and display sharing</a></p></td>
<td><p>Gets you started with resource sharing management in conversations and online meetings by using the Lync 2013 API.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-started-with-content-sharing.md">Get started with content sharing</a></p></td>
<td><p>Gets you started sharing whiteboards, PowerPoint decks, and file attachments in conversations and online meetings by using the Lync 2013 API.</p></td>
</tr>
</tbody>
</table>

## Beyond the basics: Learn more about Microsoft Lync 2013 SDK

Many of the same Lync options that can be set by the user can also be set by your application. The following table lists advanced concepts for setting many of these Lync options by using the Lync 2013 API.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concept</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="ui-suppression.md">UI suppression</a></p></td>
<td><p>Describes the coding patterns that are used to sign a user in to Lync 2013 when the Lync UI is suppressed.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-sign-in-configuration.md">Lync Server sign-in configuration</a></p></td>
<td><p>Describes how to use the sign-in configuration manager to change the Microsoft Lync Server 2013 connection settings.</p></td>
</tr>
<tr class="odd">
<td><p><a href="user-telephone-number-administration.md">User telephone number administration</a></p></td>
<td><p>Describes how to publish the local user’s phone number list.</p></td>
</tr>
<tr class="even">
<td><p><a href="custom-presence-states.md">Custom presence states</a></p></td>
<td><p>Describes how to get a localized set of availability states for display and publication.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contact-privacy-relationship-administration.md">Contact privacy relationship administration</a></p></td>
<td><p>Describes how to set the privacy relationship of the local user with another Lync user.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Lync 2013 SDK general reference](lync-2013-sdk-general-reference.md)

