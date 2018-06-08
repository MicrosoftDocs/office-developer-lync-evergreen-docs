---
title: Understand the purpose of runtime application registration
TOCTitle: Understand the purpose of runtime application registration
ms:assetid: e9be8236-03f7-4fc7-92d9-809377882cf4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933219(v=office.15)
ms:contentKeyID: 50877363
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Understand the purpose of runtime application registration

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the purpose of runtime registration of CWE applications in Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Overriding the install-time registration package<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Overriding the install-time registration package

The install-time registration package specifies the URL of the hosting IIS server or the UNC path of a network share that hosts the .xap and .html file of a CWE application. In addition, the package specifies the size of the CWE application window and the window title. You can override any of these properties at runtime to open a CWE application that is hosted at a different location, display a different CWE application title, or open with a different size. This is usually done when different versions of the CWE applications exist and are designed for different audiences.

For example, an external-facing CWE application can be designated as the default CWE application and opened by customers who join Lync 2013 conversations from federated Lync clients. The external version of the CWE application can show a simplified view of a new transaction by using conversation contextual information. The internal side of this conversation can be a sales department where a sales person launches a version of the CWE application that shows the customer’s complete purchasing history as well as new transaction data.

When the internal automation application starts a new conversation window, it can override the default registration package and load the full version of the CWE application.

The following example overrides the default package by creating an instance of the [Microsoft.Lync.Model.Extensibility.ApplicationRegistration](https://msdn.microsoft.com/en-us/library/jj293820\(v=office.15\)) class, configures it with new values, and creates an in-memory registration for the CWE application. The in-memory registration is used when the conversation window opens the extensibility tab to host the CWE application.

```csharp
        // Perform Run-Time Registration by using the ApplicationRegistration class.
        void PerformRunTimeRegistration()
        {
            // Ensure that this GUID matches the registry value entered in the previous section.
            string appname = "Contoso Internal Sales View";
            myApplicationRegistration = LyncClient.GetClient().CreateApplicationRegistration(
                "{FA44026B-CC48-42DA-AAA8-B849BCB43A21}", 
                appname);

            // Set the Conversation Window Extension properties.
            // Ensure that the internalURL parameter is valid on your computer.
            myApplicationRegistration.SetExtensibilityWindowProperties(
              @"\\contoso_sales\GenericCWEApp\GenericCWEAppTestPage.html",
              "",
              ConversationWindowExtensionSize.Medium);

            // Register the application.
            this.myApplicationRegistration.AddRegistration();
        }
```

## See also

  - [Contextual Lync conversations](contextual-lync-conversations.md)

