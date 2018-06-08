---
title: Send and update context in a UCMA conversation
TOCTitle: Send and update context in a UCMA conversation
ms:assetid: 0cd96be2-6669-4c5c-9228-b7d982b89c2a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945536(v=office.15)
ms:contentKeyID: 51541335
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Send and update context in a UCMA conversation

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn how to use Microsoft Lync 2013 SDK and Lync 2013 to participate in a Microsoft Unified Communications Managed API 4.0 conversation.

**Last modified:** February 14, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Context overview<br />
Create a conversation on the UCMA 4.0 computer<br />
Send and receive context from the Lync 2013 computer<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Context overview

The UCMA 4.0 application hosts the conversation and starts the context channel, while the Lync 2013 client responds to the **INVITE** event from UCMA 4.0 to join the conversation:

  - On the UCMA 4.0 computer, create and establish a UserEndPoint endpoint, and then add a remote endpoint to represent the Lync 2013 conversation endpoint.

  - On the Lync 2013 client, use the Conversation.GetApplicationData method to receive data and the Conversation.BeginSendContextData method to send data.

## Create a conversation on the UCMA 4.0 computer

The following steps describe how to create and manage a conversation on the UCMA 4.0 computer.

1.  Create a CollaborationPlatform instance.

2.  Create and establish an endpoint by using a previously created CollaborationPlatform instance and endpoint settings.

3.  Create a Conversation instance.

4.  Create a call, typically by using an instance of the InstantMessagingCall or AudioVideoCall class.

5.  Place a call to the remote endpoint by using the BeginEstablish method on the call, specifying the SIP URI.
    
    An **INVITE** is sent to the Lync SDK application and the first toast starts to run on the Lync 2013 computer.

6.  Create a new ConversationContextChannel instance, passing the conversation and remote endpoint as parameters.

7.  Create a ConversationContextChannelEstablishOptions instance, and then set the appropriate property values.
    
    The properties in the next example identify the application.
    
    ``` csharp
    channelOptions.ApplicationInstallerPath = "http://www.msn.com";
    channelOptions.ApplicationName = "Blue Yonder Airlines";
    channelOptions.ContextualData = "Contextual data from UCMA";
    channelOptions.RemoteConversationId = "1234";
    channelOptions.SimpleLink = "";
    channelOptions.Toast = "Some contextual data is coming in this call.";
    ```

8.  Establish the ConversationContextChannel instance by calling the BeginEstablish method and then pass the GUID in the ConversationContextChannelEstablishOptions instance.
    
    Another **INVITE** is sent and the second toast starts to run on the Lync 2013 computer.

9.  When the ConversationContextChannel instance is in the Established state, call BeginSendContextData to send contextual data to the remote endpoint.
    
    When the remote endpoint responds through the context channel, the DataReceived event on the UCMA 4.0 side is raised. This event contains contextual data in the event arguments.

10. The channel is now open and you can exchange data. When no more data will be sent, call BeginTerminate on the channel.

## Send and receive context from the Lync 2013 computer

Lync 2013 gets the application invite from UCMA 4.0, sets up the conversation window, and opens CWE with a Microsoft Silverlight application that contains information about the caller. When the SIP conversation is established, the conversation window appears, and UCMA 4.0 and Lync 2013 can exchange data over the channel both ways.

The following example shows how to use Conversation object methods to send and receive context as soon as the conversation session starts. For more information, see [Send and update context in an existing conversation](send-and-update-context-in-an-existing-conversation.md).

### Receiving content

On the Lync 2013 client, the following example shows how to use the Conversation.GetApplicationData method to receive data. A GetAppData\_Click event is sent to the Lync 2013 client.

#### Sending content

The following example also shows how to use the Conversation.BeginSendContextData method to send data. A SendData\_Click event is sent to the Lync 2013 client.

### Example

Use Conversation object methods appearing in the next example to send and receive contextual data in a conversation with a UCMA 4.0 application.

``` csharp

private void Initialize()
{
    try
    {
        _conversation = (Conversation)Microsoft.Lync.Model.LyncClient.GetHostingConversation();
        _conversation.InitialContextReceived += OnInitialContextReceived;
        _conversation.InitialContextSent += OnInitialContextSent;
        _conversation.ContextDataReceived += OnContextDataReceived;
        _conversation.ContextDataSent += OnContextDataSent;
    }
    catch (Exception ex)
    {
        System.Diagnostics.Debug.WriteLine("Exception: " + ex);
    }
}

// Occurs when an application receives context data after the initial receipt of data.
// Useful to avoid having to poll to see if more data arrived.
public void OnContextDataReceived(object sender, ContextEventArgs args)
{
    try
    {
        System.Diagnostics.Debug.WriteLine("OnContextDataReceived: AppId = " + args.ApplicationId + " DataType = " + args.ContextDataType + " Data = " + args.ContextData);
    }
    catch (Exception ex)
    {
        System.Diagnostics.Debug.WriteLine("Exception: " + ex);
    }
}

// Occurs when an application sends context data after the initial transmission of data.
public void OnContextDataSent(object sender, ContextEventArgs args)
{
    try
    {
        System.Diagnostics.Debug.WriteLine("OnContextDataSent: AppId = " + args.ApplicationId + " DataType = " + args.ContextDataType + " Data ++oncontextSent++ = " + args.ContextData);
    }
    catch (Exception ex)
    {
        System.Diagnostics.Debug.WriteLine("Exception: " + ex);
    }
}

// Occurs when an application initially sends context data.
public void OnInitialContextSent(object sender, InitialContextEventArgs args)
{
    try
    {
        System.Diagnostics.Debug.WriteLine("OnInitialContextSent: AppId = " + args.ApplicationId + " AppData ++oncontextSent++ = " + args.ApplicationData);
    }
    catch (Exception ex)
    {
        System.Diagnostics.Debug.WriteLine("Exception: " + ex);
    }
}

// Occurs when an application initially receives context data.
public void OnInitialContextReceived(object sender, InitialContextEventArgs args)
{
    try
    {
        System.Diagnostics.Debug.WriteLine("OnInitialContextReceived: AppId = " + args.ApplicationId + " AppData = " + args.ApplicationData);
    }
    catch (Exception ex)
    {
        System.Diagnostics.Debug.WriteLine("Exception: " + ex);
    }
}

private void GetAppData_Click(object sender, RoutedEventArgs e)
{
    try
    {
        // Receive data from the UCMA application.
        string appData = _conversation.GetApplicationData(AppId);
        System.Diagnostics.Debug.WriteLine("AppData = " + appData);
    }
    catch (Exception ex)
    {
        System.Diagnostics.Debug.WriteLine("Exception: " + ex);
    }
}

private void SendData_Click(object sender, RoutedEventArgs e)
{
    try
    {
        System.Diagnostics.Debug.WriteLine("Sending additional context: DataType = " + DataTypeBox.Text + " Data = " + AppDataBox.Text);

        // Send data to the UCMA application.
        // AppId parameter is the application GUID.
        // The next two parameters are text box entries from the application UI.
        // The fourth parameter is the name of the callback method.
        _conversation.BeginSendContextData(AppId, DataTypeBox.Text, AppDataBox.Text, SendAdditionalDataCallBack, null);
    }
    catch (Exception ex)
    {
        System.Diagnostics.Debug.WriteLine("Exception: " + ex);
    }
}

private void SendAdditionalDataCallBack(IAsyncResult asyncResult)
{
    if (asyncResult.IsCompleted)
    {
        _conversation.EndSendContextData(asyncResult);
        System.Diagnostics.Debug.WriteLine("Additional Context Sent successfully.");
    }
    else
    {
        System.Diagnostics.Debug.WriteLine("Additional Context Sent Failed : " + asyncResult.AsyncState);
    }
}
```

## See also

  - [Contextual Lync conversations](contextual-lync-conversations.md)

