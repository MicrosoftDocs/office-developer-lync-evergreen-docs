﻿---
title: Creating an outgoing two-party conversation
TOCTitle: Creating an outgoing two-party conversation
ms:assetid: 67b43d59-9f40-4d80-82cf-365acdae078f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465980(v=office.15)
ms:contentKeyID: 57102772
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Creating an outgoing two-party conversation


**Applies to:** Lync 2013 | Lync Server 2013

Applications can create a conversation by specifying an endpoint or by specifying an endpoint and settings for the conversation.

```csharp
// Initialize and register the endpoint, using the credentials of the user the application will be acting as.
UserEndpointSettings userEndpointSettings = new UserEndpointSettings(_userURI, userServer);
userEndpointSettings.Credential = credential;
userEndpoint = new UserEndpoint(collabPlatform, userEndpointSettings);
userEndpoint.BeginEstablish(EndEndpointEstablish, userEndpoint);

// Set up the conversation.
ConversationSettings convSettings = new ConversationSettings();
convSettings.Priority = ConversationPriority.Normal;
convSettings.Subject = "Your trip plan";

// Conversation represents a collection of modalities in the context of a dialog with one or multiple callees.
Conversation conversation = new Conversation(userEndpoint, convSettings);
```

