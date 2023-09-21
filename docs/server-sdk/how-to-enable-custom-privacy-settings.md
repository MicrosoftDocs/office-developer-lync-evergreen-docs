---
title: 'How to: Enable custom privacy settings'
TOCTitle: 'How to: Enable custom privacy settings'
ms:assetid: 33d4f997-2607-4314-93b9-1ead701646c4
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439074(v=office.15)
ms:contentKeyID: 57096232
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# How to: Enable custom privacy settings

Learn how to configure presence by using the Lync Server 2013 API. Presence helps a caller decide how to communicate with a colleague.


**Applies to:** Lync 2013 | Lync Server 2013

If the colleague’s presence is available, the caller can start the call immediately. If the colleague is away or offline, the caller can send the colleague an email. By default, Microsoft Lync 2013 displays how long a user has been away or offline along with the corresponding presence status. However, in a certain locality, this is deemed as a violation of the local privacy requirement and the time period must be removed from the presence display in Lync 2013. This process can be accomplished by using a Microsoft Lync Server 2013 SIP Application API application that filters and removes the SIP messages that contain the presence data and removes time information. This process is similar to the message payloads that are used to [How to: Enforce content integrity](how-to-enforce-content-integrity.md) and, again, can be carried out in a Microsoft SIP Processing Language (MSPL) script or in a managed code message handler. In this topic, an MSPL script is used.

Published presence data is delivered to a client by the Microsoft Lync Server 2013 instance as SIP NOTIFY or BENOTIFY request. The message payload contains a collection of presence category instances. One of them is a state category of the **AggregateState** type. This state category instance contains the lastActive attribute, when the contained presence status is Away (the availability number between 15000 and 17999) and Offline (the availability number is 18000 or higher). The lastActive attribute value records the time when the user was last active. An instance of this category appears in the next example.

```xml
<categories xmlns="http://schemas.microsoft.com/2006/09/sip/categories" uri="sip:sam@contoso.com">
  <category xmlns="http://schemas.microsoft.com/2006/09/sip/categories" name="state" instance="0" publishTime="2012-07-12T13:58:54.237">
    <state xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
          xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
          xsi:type="aggregateState" lastActive="2012-07-12T13:58:54">
       <availability>18000</availability>
    </state>
  </category>
</categories>
```

Lync uses the lastActive attribute value to compute the duration when a presentity has been in the Away or Offline state and displays the time duration to the user. The enforcement of the custom privacy requirements discussed earlier disables the display of this information.

One way to disable the display of the time duration involves removing the lastActive attribute from the **AggregateState** category instances before the subscriber receives it. As shown in the following script-only SIP application manifest example, the processing corresponds to searching for the pattern of lastActive="T" and removing any occurrences from such presence category instances.

    <?xml version="1.0"?>
    <r:applicationManifest
       r:appUri="http://www.contoso.com/RemoveLastActiveAttribute"
       xmlns:r="http://schemas.microsoft.com/lcs/2006/05">
       <r:allowRegistrationBeforeUserServices/>
       <r:serverFilter roles="ALL"/>
    
       <!-- handle NOTIFY, BENOTIFY, and SUBSCRIBE requests -->
       <r:requestFilter methodNames="NOTIFY,BENOTIFY,SUBSCRIBE"
                     strictRoute="true"
                     registrarGenerated="true"
                     domainSupported="true"/>
    
       <!-- handle 2XX response. -->
       <r:responseFilter reasonCodes="2XX"/>
    
       <!-- Script-only application. -->
       <r:scriptOnly/>
    
       <r:splScript><![CDATA[
         Log("Event", true, "Entering RemoveLastActiveAttribute.am with content: \r\n", sipMessage.Content);
         Log("Debugr", true, "Entering RemoveLastActiveAttribute.am with content: \r\n", sipMessage.Content);
         skipScan = true;
         foreach(s in GetHeaderValues(StandardHeader.Event)) {
           skipScan = !EqualString(s, "presence", true) && !EqualString(s, "vnd-microsoft-roaming-self", true);
           break;
         }
         
         if (!skipScan && ContainsString(sipMessage.Content, "lastActive", true)) {
           newContent = "";
           foreach (element in Split(sipMessage.Content, "<")) {
             if (element!= "") {
               if(!ContainsString(element, "lastActive", true)) {
                 newContent = Concatenate(newContent, Concatenate("<", element));
               }
               else {
                 index = IndexOfString(element, "lastActive=\"");
                 index1 = index + 12 + IndexOfString(SubString(element, index+12), "\"");
                 before = SubString(element, 0, index);
                 after = SubString(element, index1+1, LengthString(element)-index1-1);
                 newElement = Concatenate(before, after);
                 newContent = Concatenate(newContent, Concatenate("<", newElement));           
               }
             }
           }
           sipMessage.Content = newContent;
         }
         Log("Event", true, "Exiting RemoveLastActiveAttribute.am with new content:\r\n", sipMessage.Content);
         Log("Debugr", true, "Exiting RemoveLastActiveAttribute.am with new content:\r\n", sipMessage.Content);
         if (sipRequest) {
           ProxyRequest("");
         }
         else if (sipResponse) {
           ProxyResponse();
         }
       ]]></r:splScript>
    </r:applicationManifest>

This SIP application selects and processes only the NOTIFY, BENOTIFY requests, and the 2XX responses. The selection is specified by the \<requestFilter\> and \<responseFilter\> elements, respectively of the application manifest. The search and remove operation is carried out in the embedded MSPL script. However, not all the NOTIFY or BENOTIFY messages need to be processed. It is necessary to process only the NOTIFY or BENOTIFY messages whose EVENT header has the value of "presence" or "vnd-microsoft-roaming-self". The first type of the NOTIFY or BENOTIFY messages contains the presence state data of a remote presentity. And the second type is for the self-presence. The first foreach loop is used to ensure that only the NOTIFY or BENOTIFY message types are processed. Otherwise, the messages are routed back to the server.

The processing proceeds as follows:

1.  If the message content does not contain any "lastActive" attribute, skip the processing and route the message back to the server.

2.  Split the message content into a collection of substring, separated by "\<", and enumerate substrings to locate all the "lastActive" occurrences. This is similar to enumerating the XML element tags to identify the lastActive attributes.

3.  If a substring does not contain the lastActive attribute, prepend "\<" to the substring and append the result to the newContent variable. If the substring contains the lastActive attribute, remove the attribute (including the value) from the substring and prepend "\<" to the processed substring, and then append the result to the newContent variable.

4.  Update the message content with the newContent value.

5.  Route the updated message back to the server that will eventually deliver the message to the requesting client.


> [!NOTE]
> <P>The foreach … construct must be applied against a collection generated by a built-in MSPL function, such as a <A href="https://msdn.microsoft.com/library/hh364633(v=office.15)">Split</A> function. The string separator used in <STRONG>Split</STRONG> must be a single character. This means that the "lastActive" phrase cannot be used. Although it is possible to use another single character in <STRONG>Split</STRONG> to generate the collection, the use of "&lt;" is a simple approach in the context of MSPL. Although MSPL is limited in terms of processing messages, its use invokes less overhead in the processing of messages. The managed code message handler, on the other hand, supports more advanced processing capabilities, but its invocation will more likely incur more overhead.</P>



The foreach loop shown above can be replaced with a while loop. For more information, see the **RemoveLastActiveAttribute** sample in the Code Gallery on MSDN.

## See also

#### Concepts

[Scenarios for using the Lync Server 2013 API](scenarios-for-using-the-lync-server-2013-api.md)

[How to: Enforce content integrity](how-to-enforce-content-integrity.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

#### Other resources

[Video: Use an MSPL Script to Enforce Custom Privacy Settings](http://www.microsoft.com/resources/msdn/office/media/video/video.html?cid=ldc%26from=mscomldc%26videoid=235a58e8-1ca5-4aac-aed5-f3df29936a91)

