﻿---
title: Registering for conversation events
TOCTitle: Registering for conversation events
ms:assetid: ec21df6c-1ec7-4a8a-96cd-11daf5fb2ce1
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465983(v=office.15)
ms:contentKeyID: 57102787
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Registering for conversation events


**Applies to:** Lync 2013 | Lync Server 2013

Conversations expose several events that can be useful to an application, and may represent a good handle for the application developer to invoke business logic, or adjust a user interface. For example, the [StateChanged](https://msdn.microsoft.com/library/hh365987\(v=office.15\)) event is raised when the state of the conversation changes, and the [PropertiesChanged](https://msdn.microsoft.com/library/hh384248\(v=office.15\)) event is raised when a property of the conversation such as [Subject](https://msdn.microsoft.com/library/hh349381\(v=office.15\)) or [Id](https://msdn.microsoft.com/library/hh366404\(v=office.15\)) changes.

The following code demonstrates registering for the PropertiesChanged event and the implementation of a simple handler for this event.

```csharp
conversation.PropertiesChanged += Conversation_PropertiesChanged;

private void Conversation_PropertiesChanged(object sender, PropertiesChangedEventArgs<ConversationProperties> e)
{
  if (e.ChangedPropertyNames != null)
  {
    //Update the property from property changed event
    foreach (string propertyName in e.ChangedPropertyNames)
    {
      switch (propertyName)
      {
        case ConversationProperties.ConversationIdPropertyName: 
          Console.WriteLine("Conversation id changed to {0}", e.Properties.Id);
          break;
        case ConversationProperties.ConversationPriorityPropertyName: 
          Console.WriteLine("Conversation priority changed to {0}", e.Properties.Priority);
          break;
        case ConversationProperties.ConversationSubjectPropertyName:
          Console.WriteLine("Conversation subject changed to {0}", e.Properties.Subject);
          break;
        case ConversationProperties.ConversationActiveMediaTypesPropertyName:
          Console.WriteLine("Conversation active media types property name changed to");
          foreach (string activeMedia in e.Properties.ActiveMediaTypes)
          {
            Console.WriteLine(activeMedia);
          }
          break;
        default:
          //Should not reach here
          Debug.Assert(false, "property name not expected");
          break;
      }
    }
  }
}
```

