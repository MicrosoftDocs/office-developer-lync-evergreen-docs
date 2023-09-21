---
title: Troubleshooting Lync 2013 SDK development issues
TOCTitle: Troubleshooting Lync 2013 SDK development issues
ms:assetid: e6718d84-5efe-4e36-932e-110b223be625
ms:mtpsurl: https://msdn.microsoft.com/library/Dn609830(v=office.15)
ms:contentKeyID: 61218832
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Troubleshooting Lync 2013 SDK development issues

**Applies to:** Lync 2013 | Lync Server 2013

The following sections describe common issues developers may run into when developing applications using the Microsoft Lync 2013 SDK.

## COM exceptions

This section explains how to troubleshoot some known COM exceptions.

### Generic COM Exception. Code 0x80EE0066

This error may occur when you start a Lync custom application that uses UI suppression. The TechNet article [FSOCS troubleshooting](http://technet.microsoft.com/library/cc676984.aspx) describes this as a DNS issue and provides some recommendations.

#### Resolution

1.  Disable Lync client UI suppression. For more information on UI suppression, see the MSDN article [UI suppression](../desktop/ui-suppression.md). For more information about how to edit the registry, see the MSDN article [How to Modify the Windows Registry](http://support.microsoft.com/kb/136393).

2.  Start Lync, then close Lync.

3.  Enable UI suppression.

4.  Retry the application.

### Generic COM Exception. Code 0x800706F7

This error may occur in applications that use the [VideoWindow](https://msdn.microsoft.com/library/office/microsoft.lync.model.conversation.audiovideo.videowindow_di_3_uc_ocs14mreflyncclnt.aspx) class. This error was documented in two Knowledge Base articles:

- [The call operation fails with error code "0x800706f7"](http://support.microsoft.com/kb/2457836)
- [Error code 0x800706f7 when you run an application](http://support.microsoft.com/kb/2868239/nl)

Two possible fixes were described in forum postings:

- Move the application project from \\Program Files(x86) to a location in the Users folder.
- Disable the User Account Control‎ and select "Allow unsafe code" in the Visual Studio [project options pane](http://msdn.microsoft.com/library/kb4wyys2.aspx).

## Using Lync client methods

### GetHostingConversation()

Users report errors like "\<object\> does not contain a definition for ‘GetHostingConversation’" or that the method returns a null . The following two notes may help resolve errors such as these.

- The GetHostingConversation method is available only in LyncSilverlight applications. The documents describe this method as "called in an application running in the Lync conversation extension area". The Conversation Window Extension (CWE) is available only in a Silverlight application. Therefore, by design the **GetHostingConversation** method is also only available in a Silverlight application.

- The **GetHostingConversation** method returns a null if the conversation is not fully established. Call **GetHostingConversation** too early, and it also returns a null . A good rule of thumb is that when the application in the CWE is open, the [Conversation](chttps://msdn.microsoft.com/library/office/microsoft.lync.model.conversation.conversation_di_3_uc_ocs14mreflyncctrsl.aspx) object is available, and **GetHostingConversation** will work as expected.

### GetClient ()

When trying to access the [LyncClient.GetClient](https://msdn.microsoft.com/library/office/microsoft.lync.model.lyncclient.getclient_di_3_uc_ocs14mreflyncctrsl.aspx) method, you may receive a null object or an error 'RPC Server is unavailable (0x800706BA)'. If the Lync client process is shut down and restarted you do not get a valid Lync client object at least until a user is logged in, and there may also be a short delay past that moment.

One workaround is to get a property value from the client after it is invalid. This should cause an exception, and at that time Lync should invalidate the cached object. A valid client should now be available. Also, consider using code such as the following simple loop:

```csharp
    _lyncClient = LyncClient.GetClient();
                       
    while (_lyncClient.Capabilities == LyncClientCapabilityTypes.Invalid)
    {
        System.Threading.Thread.Sleep(100);
        _lyncClient = LyncClient.GetClient();
    }
```

If your application is running on a computer where the Lync client is not installed and you receive an error like 'ClientNotFoundException on Microsoft. Lync.Model.LyncClient.GetClient() ("The host process is not running")’, ensure the application includes references to the following components:

- Microsoft.Lync.Model
- Microsoft.Rtc.Collaboration
- Microsoft.Rtc.Collaboration.Presence
- Microsoft.Rtc.Signaling

## Visual Studio 2013 compatibility

Users report errors when installing Lync 2013 SDK on a computer where Visual Studio 2013 is installed. Lync 2013 SDK requires Microsoft Visual Studio 2010 SP1 or Visual Studio 2012. For the full list of Lync 2013 SDK prerequisites, see the Application Development section in the MSDN article [Get started with Lync 2013 SDK](../desktop/get-started-with-lync-2013-sdk.md).

## See also

- [Lync 2013 technical articles](lync-2013-technical-articles.md)
- [Lync 2013 SDK documentation](../desktop/lync-2013-sdk-documentation.md)
- [Developer code samples](http://code.msdn.microsoft.com/)
- [NextHop](http://blogs.technet.com/b/nexthop/)

