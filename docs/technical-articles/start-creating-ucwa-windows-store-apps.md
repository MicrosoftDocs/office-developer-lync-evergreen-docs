---
title: Start creating UCWA Windows Store apps
TOCTitle: Start creating UCWA Windows Store apps
ms:assetid: ae341e4b-e90e-4efe-87d4-5d2f797cba18
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn551187(v=office.15)
ms:contentKeyID: 60829953
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Start creating UCWA Windows Store apps

In this article, you will learn how to build a simple Windows Store app in C\#/XAML and XML. The steps illustrated here are required of all UCWA applications. It is intended as a self-contained introduction to building and deploying a UCWA application targeted for Windows Store.


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
What is involved in signing in a user to UCWA?  
In this article  
Additional resources  

Demonstrated UCWA programming features include how to make asynchronous calls to sign in and then to get the self-presence, personal note and the list of telephone numbers of the signed-in user. Some basic requirements of Windows Store apps are also examined in the context of a UCWA application. Specifically, you will learn how to carry out the following programming tasks:

  - **Create and Test a Windows Store application using C\#/XAML**
    
    The application has a UI component based on the basic Windows Store app UI template. It takes a user name and password from a user and logs the user in to UCWA. The application takes advantage of the Windows Store app API features to cache or persist the user login information and other application data to render fluid user experiences.
    
    Creating and deploying Windows Store apps involves a somewhat different process than a Windows desktop application. This tutorial is self-contained and does not require extensive prior knowledge of using Windows Store app APIs. However, if you’re new to building Windows Store apps, you may find it helpful to read the articles listed in the Additional resources section.

  - **Sign in to UCWA and inspect the local user data and presence**
    
    Sign-in is the first step that every UCWA application must perform before other UCWA features become available. The process involves discovering the UCWA service address, getting the user authenticated, and creating a UCWA application resource.
    
    Programming using UCWA involves initiating HTTP requests and processing responses to access and operate UCWA resources. To do so, this application uses [HttpWebRequest](http://msdn.microsoft.com/en-us/library/system.net.httpwebrequest\(v=vs.110\).aspx) and [HttpWebResponse](http://msdn.microsoft.com/en-us/library/system.net.httpwebresponse\(v=vs.110\).aspx) as well as other classes in the [System.Net namespace](http://msdn.microsoft.com/en-us/library/system.net\(v=vs.110\).aspx) for Windows Store apps. To showcase the versatility of UCWA, the application chooses XML as the content type for transporting the HTTP messages and uses the [System.Xml.Linq](http://msdn.microsoft.com/en-us/library/system.xml.linq\(v=vs.110\).aspx) namespace to parse the UCWA resources.

## What is involved in signing in a user to UCWA?

Signing in is the first step to create any UCWA application. It amounts to getting a user authenticated using one of the following authentication types:

  - Using the user-supplied Lync account name and password

  - Using integrated Windows credentials

  - Using user’s account name and a conference ID for joining a meeting anonymously

  - Using passive authentication supported by Active Directory Federation Service

In this article, the password-based authentication is used. Once the user is authenticated, the application is returned an OAuth security token. The UCWA application must provide this security token in any of the subsequent HTTP requests. When the token expires, the application must be renew it.

Before the authentication can take place, the UCWA application must first locate the UCWA service enabled on the user’s domain. The process is known as auto-discovery of the UCWA [root](http://ucwa.skype.com/documentation/gettingstarted-rooturl) resource and will be illustrated in this article.

A successful authentication must also be followed by obtaining a UCWA [application](http://ucwa.skype.com/documentation/resources-application) resource representing an instance of the application bound to the local endpoint of the signed-in user. When the application times out, the application resource must be updated. This may involve getting the user re-authenticated.

Because UCWA-specific operations are carried out as HTTP requests and responses, it is natural to encapsulate them in a separate type. In this article, they are exposed as asynchronous methods on a Transport class, which can be reused for other applications as well. The asynchronous behavior is built upon the async/await[pattern](http://msdn.microsoft.com/en-us/library/vstudio/hh191443.aspx). It is required to ensure that the Windows Store app be responsive.

A Windows Store app undergoes a much frequent change of states than traditional desktop applications. Managing the application’s states and life cycle is important to enable the Windows Store app fluid and to comply with the REST-ful requirements of UCWA.

## In this article

This article contains the following topics.

  - [Create a UCWA Windows Store app project](create-a-ucwa-windows-store-app-project.md)

  - [Enable fluid user interface](enable-fluid-user-interface.md)

  - [Ensure responsive HTTP operations](ensure-responsive-http-operations.md)

  - [Implement the UCWA sign-in workflow](implement-the-ucwa-sign-in-workflow.md)

  - [Putting it all together](putting-it-all-together.md)

## Additional resources

  - [Create your first Windows Store app using C\# or Visual Basic](http://msdn.microsoft.com/en-us/library/windows/apps/hh974581.aspx): If you’re new to building Windows Store apps, I highly recommend this step-by-step guide with clear instructions to creating a Windows RT application using C\# or Visual Basic.

  - [Get a developer license (Windows Store apps)](http://msdn.microsoft.com/en-us/library/windows/apps/hh974578.aspx): To install and test a Windows RT application before submitting it to Windows Store, you can get a developer license for each machine on which you intent to run the app. This article tells you how to get and renew a developer license, valid for a 30-day period, from Visual Studio or at a command prompt.

  - [How to Add and Remove Apps](http://technet.microsoft.com/en-us/library/hh852635.aspx): This article details the requirements and steps necessary for deploying an enterprise (or LOB) application using the mechanism of side-loading and, therefore, bypassing Windows Store all together. This could be a common scenario for UCWA apps.

  - [Manage Client Access to the Windows Store](http://technet.microsoft.com/en-us/library/hh832040.aspx): In addition to configuring side-loading for deploying your Windows RT application without going through Windows Store, this article provides an entry point to other information useful for managing app access to Windows Store in an enterprise environment.

  - [Manage app lifecycle and state (Windows Store apps using C\#/VB and XAML)](http://msdn.microsoft.com/en-us/library/windows/apps/hh986968.aspx): It offers an introductory discussion of Windows app lifecycle and state management issues, with a hands-on tutorial.

  - [UCWA API Resource reference library](http://ucwa.skype.com/documentation/api-reference): This is the official UCWA documentation site where you can find detailed specification of all the UCWA resources.

  - [UCWA Dev Portal](http://ucwa.skype.com/): This is the official UCWA development portal where you can find interactive demo and sample code, written in JavaScript and JSON. You can also access the community forum for UCWA developers.

  - [What is UCWA API?](http://ucwa.skype.com/documentation/what-is-lync-ucwa-api): This is the landing page of the official UCWA documentation, where you can find more detailed discussions of the requirements, features and architecture of UCWA.

