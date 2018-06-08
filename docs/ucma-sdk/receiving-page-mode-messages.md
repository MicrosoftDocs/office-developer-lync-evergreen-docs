---
title: Receiving page-mode messages
TOCTitle: Receiving page-mode messages
ms:assetid: 88a178b6-766c-4f1b-b36b-d8bd945c5faa
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466058(v=office.15)
ms:contentKeyID: 57103051
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Receiving page-mode messages


**Applies to:** Lync 2013 | Lync Server 2013

Subscribing to the event amounts to registering for notification when a [MessageReceived](https://msdn.microsoft.com/en-us/library/hh350010\(v=office.15\)) event is raised, and implementing a handler for this event. The following is a simple code example that illustrates this process.

```csharp
RealTimeEndpoint endpoint = ...; // Assumed to be created elsewhere.

endpoint.MessageReceived += pageMode_MessageReceived;

void pageMode_MessageReceived(object sender, MessageReceivedEventArgs e)
{
  if ((e.ContentType.MediaType.CompareTo("text/plain") == 0) &&
      (e.ContentType.CharSet.CompareTo("utf-8") == 0) &&
      (e.HasTextBody == true))
  {
    string msg = Encoding.UTF8.GetString(e.GetBody());
    Console.WriteLine(msg);
  }

  else 
  {
    // Handle other media types and other character encoding types.
  }
}
```

