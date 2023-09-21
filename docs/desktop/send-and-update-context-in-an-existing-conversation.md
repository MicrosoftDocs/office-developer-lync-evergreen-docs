---
title: Send and update context in an existing conversation
TOCTitle: Send and update context in an existing conversation
ms:assetid: cb42a093-51ce-4526-be46-ca6f27d2a4ac
ms:mtpsurl: https://msdn.microsoft.com/library/JJ945576(v=office.15)
ms:contentKeyID: 51541393
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Send and update context in an existing conversation

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn how to send and update data in existing conversations by using Microsoft Lync 2013 SDK methods.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Context overview<br />
Send and update data in an existing conversation<br />
Add context to a conversation<br />
Send a context link<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Context overview

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Method</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj275891(v=office.15)">BeginSendInitialContext(IEnumerable&lt;KeyValuePair&lt;ContextType, Object&gt;&gt;, AsyncCallback, Object)</a></p></td>
<td><p><strong>BeginSendInitialContext</strong> is the setup method. Call it first. This method can be used multiple times in a single conversation, for example, if there is a change in subject and additional data is needed. The data limit is 2,000 characters.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/jj278336(v=office.15)">BeginSendContextData(String, String, String, AsyncCallback, Object)</a></p></td>
<td><p>Use <strong>BeginSendContextData</strong> for more advanced scenarios, such as implementing a command and response protocol, or exchanging large amounts of data. It can only be used after a session is established. However, it can be used again in an existing conversation as often as needed. The data limit is 64,000 characters.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BeginStartConversation(String, Int32, AsyncCallback, Object)</strong></p></td>
<td><p>Use the <strong>BeginStartConversation</strong> method and the values of the <a href="https://msdn.microsoft.com/library/jj276319(v=office.15)">AutomationModalitySettings</a> enumerator to add rich context to Lync SDK conversations.</p></td>
</tr>
</tbody>
</table>

## Send and update data in an existing conversation

The following example shows how to use the **Conversation.BeginSendInitialContext** method.

```csharp
Dictionary<ContextType, object> context = new Dictionary<ContextType, object>();
context.Add(ContextType.ApplicationId, "{d0722164-f660-470f-a933-e4853f215b77}");
context.Add(ContextType.ApplicationData, "Some data string");
IAsyncResult res = conversation.BeginSendInitialContext(context, null, null);
```

The following example implements the **Conversation.BeginSendContextData** method.

```csharp
string appId = "{d0722164-f660-470f-a933-e4853f215b77}";
string appData = "Some additional data";
IAsyncResult res = conversation.BeginSendContextData(appId, "text/plain", appData, SendAdditionalContextCallback, null);

// Callback method
public void SendAdditionalContextCallback(IAsyncResult res)
{
  conversation.EndSendAdditionalContextData(res);
}
```

### Events

Use the **OnInitialContextReceived** and **OnInitialContextSent** events on the **Conversation** object to notify the application that the conversation received and sent data.

## Add context to a conversation

The following example shows how to use the **BeginStartConversation** method and the values of the [AutomationModalitySettings](https://msdn.microsoft.com/library/jj276319\(v=office.15\)) enumerator to add rich context to Lync SDK conversations. Also, use the **Conversation.BeginSendInitialContext** method.

```csharp
Dictionary<AutomationModalitySettings, object> _ModalitySettings = new Dictionary<AutomationModalitySettings, object>(); 

// Add the process ID to the modality settings for the conversation.
_ModalitySettings.Add(ApplicationId, "{40499119-4B60-45a6-9A7A-DC7A384D5670}";

// Add application data.
_ModalitySettings.Add(AutomationModalitySettings.ApplicationData, "some application data with you.");

// Declare the string array.
string[] invitees = {″elise@contoso.com"};

IAsyncResult ar =  _Automation.BeginStartConversation(
                    _ChosenMode
                    , invitees
                    , _ModalitySettings
                    , null
                    , null);

// Block main thread until the conversation starts.
_Automation.EndStartConversation(ar);
```

## Send a context link

To send a context link, use the **ContextType.HyperLink** enumeration.

```csharp
Dictionary<ContextType, object> context = new Dictionary<ContextType, object>();
context.Add(ContextType.HyperLink, "http://contoso.com");
IAsyncResult res = conversation.BeginSendInitialContext(context, SendContextCallback, null);
```

## See also

  - [Contextual Lync conversations](contextual-lync-conversations.md)

