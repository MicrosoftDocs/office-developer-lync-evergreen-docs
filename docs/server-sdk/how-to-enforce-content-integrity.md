---
title: 'How to: Enforce content integrity'
TOCTitle: 'How to: Enforce content integrity'
ms:assetid: 55722aa5-2e9d-4c75-bc5f-ff4458a7bf68
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439072(v=office.15)
ms:contentKeyID: 57096231
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Enforce content integrity

Learn how a server-side script-only SIP application or managed SIP application can be used to manage message payloads and message content.


**Applies to:** Lync 2013 | Lync Server 2013

An organization might want to use policies that control the way instant messaging is used by employees. For example, a security policy might disable a link to an external website. This process involves searching and replacing specified patterns in the message payload to modify the message content. A Microsoft Lync Server 2013 SIP Application API application can be used to implement this process. Depending on the application requirement, either a server-side script-only SIP application or managed SIP application can be used. The following managed SIP application example shows how to set up this process.

## Use a managed SIP application to enforce content integrity

In this example, HTML is the content type of the SIP messages. In a managed SIP application, the Microsoft SIP Processing Language (MSPL) script delegates the message handling to a managed code handler in the following example.

``` 
   <r:splScript><![CDATA[

   Log("Event", false, "Entering DisableHrefLinksM...", sipMessage.Content);

    if (sipRequest) {
      Dispatch("DisableHrefLinksOnRequest");
    }

    if (sipResponse) {
      Dispatch("DisableHrefLinksOnResponse");
    }
   Log("Event", false, "Exit DisableHrefLinksM.");
   
]]></r:splScript>
```

DisableHrefLinksOnRequest is the name of the corresponding managed code message handler for the sipRequest object and DisableHrefLinksOnResponse is the name of the corresponding managed code message handler for the sipResponse object. In the following example, two managed code message handlers are used.

``` 
        public void DisableHrefLinksOnRequest(object sender, RequestReceivedEventArgs e)
        {
            e.Request.Content = SearchReplaceHrefLinks(e.Request.Content);
            e.ServerTransaction.CreateBranch().SendRequest(e.Request);

        }
        
        public void DisableHrefLinksOnResponse(object sender, ResponseReceivedEventArgs e)
        {
            e.Response.Content = SearchReplaceHrefLinks(e.Response.Content);
            e.ClientTransaction.ServerTransaction.SendResponse(e.Response);
        }
        string SearchReplaceHrefLinks(string content)
        {
           string newContent = null;
           foreach (string segment in content.Split(new string[] {"<a href="}, StringSplitOptions.None)) {
              if (newContent==null) {
                newContent = segment;
              }
              else {
                int index1 = segment.IndexOf(@">");
                int index2  = segment.IndexOf(@"</a>");
                string linkUri = segment.Substring(0, index1);
                string linkText = segment.Substring(index1+1, index2-index1-1);
                newContent += linkText + " (" + linkUri + ")";
                newContent += segment.Substring(index2+4, segment.Length - index2 -4);
              }
            }
            return newContent;
        }
```

The previous managed code example implements search and replace logic by locating the HTML anchor tag, and then retrieving the link text and link URI before removing the anchor tag and rewriting the link text and link URI as plain text. However, the managed code is not limited to this single approach. You can also use string manipulations, such as Regular Expression and the System.Text namespace, in the managed code.

## See also

#### Concepts

[Scenarios for using the Lync Server 2013 API](scenarios-for-using-the-lync-server-2013-api.md)

[Modify SIP message content (ContentModification sample)](modify-sip-message-content-contentmodification-sample.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

