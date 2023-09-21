---
title: 'How to: Add enhanced presence to a Web application'
TOCTitle: 'How to: Add enhanced presence to a Web application'
ms:assetid: 5febdddb-c880-4a94-a197-f0c2a4380f83
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933063(v=office.15)
ms:contentKeyID: 50877193
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- html
---

# How to: Add enhanced presence to a Web application

Learn how to add Microsoft Lync Controls to an existing HTML Web application using Microsoft Silverlight.



**Applies to**: Lync 2013 | Lync Server 2013

<div class="caption">
Watch the video: Add Lync Controls to a Web Application
</div>
<br />

> [!VIDEO https://www.microsoft.com/videoplayer/embed/c3d4ed0f-b3c8-43c4-af53-36425f014575]


## Prerequisites

For a list of prerequisites, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

## Start with an existing Web application

You can use your own Web application or create one using the following HTML. The object tag contains the Silverlight application and determines how much space it occupies in the HTML page.

```html
<html>
<head>
</head>
<body>
<object width="300" height="300" 
data="data:application/x-silverlight-2," 
type="application/x-silverlight-2" >
<param name="source" value="myApplication.xap"/>
</object>
<p>Text in an HTML paragraph element</p>
</body>
</html>
```

## Create a Silverlight application

Create a Silverlight application and add a [MyStatusArea](https://msdn.microsoft.com/library/hh363503\(v=office.15\)) control to it. For more information, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

## Embed the presence application in the HTML page

In the HTML page, add a reference to the Silverlight project .xap file.

### To embed the presence application in the HTML page

1.  Build the Silverlight application created earlier.
    
    This creates the .xap file needed in the next steps.

2.  In the Silverlight project’s Bin/Debug folder, locate the .xap file.

3.  In the Web application, update the value attribute in the param element to point to the .xap file identified in the previous step.

4.  Launch the Web application.
    
    See the MyStatusArea control embedded in the rendered page.

## Next steps

After adding the presence control to a Silverlight page, the next tasks are to add presence controls for other users, add a contact list that is customized to show team members, and start conversations with those users whose presence shows as available.

  - [How to: Get the enhanced presence of a Lync user](how-to-get-the-enhanced-presence-of-a-lync-user.md)

  - [How to: Display a customized list of team contacts in Lync SDK](how-to-display-a-customized-list-of-team-contacts-in-lync-sdk.md)

  - [How to: Use Lync Controls to start a conversation](how-to-use-lync-controls-to-start-a-conversation.md)

## See also

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

