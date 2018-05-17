---
title: Consume data and handle events in a contextual conversation
TOCTitle: Consume data and handle events in a contextual conversation
ms:assetid: f74a1c56-2ddd-42fe-b47b-1c4a2bc744a1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945584(v=office.15)
ms:contentKeyID: 51541409
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Consume data and handle events in a contextual conversation

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Use Microsoft .NET Framework code and Microsoft Lync 2013 SDK to consume contextual data and handle events in a Lync 2013 conversation.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Send and access contextual data<br />
Handle the ConversationAdded event<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>


## Send and access contextual data

Use [Conversation](conversation-class-microsoft-lync-model-conversation_2.md) object methods and events to send and access contextual data in a Lync 2013 conversation.

### Sending data

Use the BeginSendInitialContext and BeginSendContextData methods to send and update data in existing conversations. For more information, see [Send and update context in an existing conversation](send-and-update-context-in-an-existing-conversation.md).

### Accessing data

On the receiver side, use the [InitialContextReceived](conversation-initialcontextreceived-event-microsoft-lync-model-conversation_2.md) event to access data.

``` csharp
public void OnInitialContextReceived(Microsoft.Lync.Model.Conversation.Conversation eventSource, Microsoft.Lync.Model.Conversation.ContextEventArgs eventData)
        {
            try
            {
                string appId = eventData.ApplicationId;
                string appData = eventData.ApplicationData;
                Log(Color.Blue, string.Format(
                    "ContextualConversation_OnContextReceived AppId={0}, AppData={1}",
                    appId, appData
                    ));
            }
            catch (Exception ex)
            {
                Log(ex);
            }
        }
```

On the sender side, use the [InitialContextSent](conversation-initialcontextsent-event-microsoft-lync-model-conversation_2.md) event to access data.

``` csharp
public void OnInitialContextSent(Microsoft.Lync.Model.Conversation.Conversation eventSource, Microsoft.Lync.Model.Conversation.ContextEventArgs eventData)
        {
            try
            {
                string appId = eventData.ApplicationId;
                string appData = eventData.ApplicationData;
                Log(Color.Blue, string.Format(
                    "ContextualConversation_OnContextSent AppId={0}, AppData={1}",
                    appId, appData
                    ));
                string sourceAppData = eventSource.GetApplicationData(appId);
            }
            catch (Exception ex)
            {
                Log(ex);
            }
        }
```

Use the GetApplicationData method on the Conversation object to access the most recent initial context. The most recent initial context is what the user has just sent or received using the BeginSendInitialData or BeginStartConversation methods. GetApplicationData returns no other context sent or received through BeginSendContextData.

### Use LaunchLink to access application data

Each LaunchLink has data embedded in the start URL. Clicking the link starts the application together with the corresponding application data and raises the [ConversationContextLinkClicked](conversation-conversationcontextlinkclicked-event-microsoft-lync-model-conversation_2.md) event. LaunchLink appears in the conversation history when a user sends or receives a contextual conversation tied to a contextual application whose registration data contains a Path value. Clicking the link executes the Path+Parameters values. If there is a %AppData% parameter in the Parameters value, it is replaced with the data embedded in the LaunchLink. The click also raises the LinkClicked event, which delivers the application data to the application if it is running. If the application is not running, the event is missed.

``` csharp
public void OnConversationContextLinkClicked(uc.Conversation eventSource, uc.ContextEventData eventData)
        {
            try
            {
                Log(Color.Blue, string.Format("ContextualConversation_OnLaunchLinkClicked AppId={0}, AppData={1}",
                    eventData.ApplicationId, eventData.ApplicationData
                    ));
            }
            catch (Exception ex)
            {
                Log(ex);
            }
        }
```

## Handle the ConversationAdded event

Use the [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event for conversation handling. ConversationAdded provides access to [Conversation](conversation-class-microsoft-lync-model-conversation_2.md) and [ConversationWindow](conversationwindow-class-microsoft-lync-model-extensibility_2.md) objects. To review example code that shows how to use the ConversationAdded event, see [How to: Start a Lync IM conversation](how-to-start-a-lync-im-conversation.md).

## Additional resources

  - [Contextual Lync conversations](contextual-lync-conversations.md)

