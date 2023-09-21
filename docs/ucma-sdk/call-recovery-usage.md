---
title: Call recovery usage
TOCTitle: Call recovery usage
ms:assetid: 6891b977-0949-411a-8525-52414753d7d5
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466066(v=office.15)
ms:contentKeyID: 57103058
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Call recovery usage


**Applies to:** Lync 2013 | Lync Server 2013

For an application that intends to wait for dialog healing, an event handler for the [RouteSetStatusChanged](https://msdn.microsoft.com/library/hh382697\(v=office.15\)) event should be patterned as shown in the following code example.

```csharp
private void RouteSetStatusChangedHandler(object sender, RouteSetStatusChangedEventArgs e)
{
  if(e.RouteSetStatus == RouteSetStatus.Recovering)
  {
    // Hold off sending any messages, and potentially implement a shutdown timer (to ensure that calls eventually terminate).
  }
  
  if(e.RouteSetStatus == RouteSetStatus.Healthy)
  {
    // Send any pending messages and resume normal processing.
  }
  

}
```

If the application is less concerned about message order, there is no need to hold pending messages if the status received is **Recovering**. Simply continue retrying until the session is terminated, keeping in mind that recovery attempts continue indefinitely. The application should eventually terminate the call if the route does not recover. The application can terminate the call based on a timer or other criterion, such as when the media flow is terminated.

