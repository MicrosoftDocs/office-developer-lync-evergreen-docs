---
title: Add custom commands to Lync menus
TOCTitle: Add custom commands to Lync menus
ms:assetid: 111f20b1-07c8-452b-bb8d-4a52308311f5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945535(v=office.15)
ms:contentKeyID: 51541334
ms.date: 09/02/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Add custom commands to Lync menus

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Use custom commands embedded in the Lync 2013 UI to launch applications on the Microsoft Windows desktop. Custom commands are menu items added by the developer to the Lync 2013 UI.

**Last modified:** August 29, 2014

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Adding custom commands<br />
Using custom commands<br />
Removing custom commands<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Adding custom commands

To add a custom command for an application, add a registry subkey and the registry entries described in this topic.

### Registry subkey

The subkey is the application GUID, added at the following locations:

  - For 32bit OS: **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps**

  - For 64bit OS: **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps**

### Registry entries

Under each GUID subkey, add the entries described in the following table.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Entry</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>REG_SZ</p></td>
<td><p>The name of the application as it appears in the Lync 2013 UI.</p></td>
</tr>
<tr class="even">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p>The full path of the application along with parameters, including the default parameters of <em>%user-id%</em> and <em>%contact-id%</em>. The parameters pass a string representing the SIP URI of the user signed in to Lync 2013 and the selected contact or contacts to the application launched. With Path values, a shell execute command might fail because of characters that have special meaning in the shell environment. Be sure to wrap the default parameters in double quotes to avoid shell execution failure. The following examples show usage for HTML and .exe paths.</p>
<pre><code>c:\\ext_menu.exe /userId=”%user-id%” /contactId=”%contact-id%”</code></pre>
<pre><code>http://localhost/Test/Sample1.html?userId=%user-id%;contactId=%contact-id%</code></pre></td>
</tr>
<tr class="odd">
<td><p>ApplicationType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = Executable, 1 = Protocol.</p></td>
</tr>
<tr class="even">
<td><p>ApplicationInstallPath</p></td>
<td><p>REG_SZ</p></td>
<td><p>The full path of the executable, which is required if <strong>ApplicationType</strong> is 0.</p></td>
</tr>
<tr class="odd">
<td><p>SessionType</p></td>
<td><p>DWORD</p></td>
<td><ul>
<li><p>0 = local session. The application is launched on this computer.</p></li>
<li><p>1 = two-party session. Microsoft Lync 2013 SDK launches the application locally and prompts the other user to launch the application on their computer.</p></li>
<li><p>2 = multi-party session. Lync SDK launches the application locally and prompts the other users to launch the application on their computers.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>ExtensibleMenu</p></td>
<td><p>REG_SZ</p></td>
<td><p>A semicolon-delimited list of places where the command appears. Possible values include <strong>MainWindowActions</strong>, <strong>MainWindowRightClick</strong>, <strong>ConversationWindowActions</strong>, and <strong>ConversationWindowRightClick</strong>.</p>
<p>If <strong>ExtensibleMenu</strong> is not defined, the default values of <strong>MainWindowRightClick</strong> and <strong>ConversationWindowActions</strong> are used.</p></td>
</tr>
</tbody>
</table>

For example, see the following Registry Editor (.reg) file results.

    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps\{3E0352E8-21F3-4E00-AA46-2ADA7085C9AD}]
    "Name"="Contoso Custom Application"
    "ApplicationType"=dword:00000000
    "ApplicationInstallPath"="C:\\ExtApp1.exe"
    "Path"="C:\\ExtApp1.exe /userId=%user-id% /contactId=%contact-id%"
    "SessionType"=dword:00000000
    "ExtensibleMenu"="ConversationWindowRightClick;MainWindowRightClick"

**Custom Parameters for the Path Registry Entry**

Custom parameters *%param1%* through *%param7%* can be set for each application.

    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps\{96DC330B-0A57-4A26-963B-75A109CD3C30}]
    "Name"="Your Application Name "
    "Path"="C:\\Program Files (x86)\\YourApplication\\ps.exe %param1%"
    "ToolTip"="tooltip text"
    "ApplicationType"=dword:00000000
    "SessionType"=dword:00000002
    "Extensiblemenu"="MainWindowActions;MainWindowRightClick;ConversationWindowActions;ConversationWindowContextual;ConversationWindowRightClick;ConversationWindowButton"

These parameters will be replaced by values added in a separate key under **HKEY\_CURRENT\_USER** as shown in the following example and passed to the recipient in the **appINVITE** message.

    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters\{96DC330B-0A57-4A26-963B-75A109CD3C30}]
    "param1"="256341"

## Using custom commands

The following table describes how to launch an application with a given **ExtensibleMenu** value.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>ExtensibleMenu value</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>MainWindowActions</strong></p></td>
<td><p>In the upper-right corner of the Lync 2013 conversation window, click the <strong>Show menu</strong> button, point to <strong>Tools</strong>, and then click the custom command.</p></td>
</tr>
<tr class="even">
<td><p><strong>MainWindowRightClick</strong></p></td>
<td><p>In the conversation window, right-click a contact in the <strong>Contact List</strong> or <strong>Search Results</strong> pane, and then click the custom command.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConversationWindowActions</strong></p></td>
<td><p>In the lower-right corner of the conversation window, click the <strong>More options</strong> ellipse, point to <strong>Actions</strong>, and then click the custom command.</p></td>
</tr>
</tbody>
</table>

### Retrieving SIP URIs in the custom application

To retrieve the *%user-id%* and *%contact-id%* arguments, add code to the application launched by the custom command.

```csharp
static void Main(string[] args)
{
  if (null == args || args.Length == 0)
  {
    Console.WriteLine("Args is empty");
  }
  else
  {
    foreach (string arg in args)
    {
      Console.WriteLine("Arg: " + arg);
    }
  }
  Console.ReadLine();
}
```

## Removing custom commands

Removing the GUID subkey removes the appropriate custom commands from the Lync 2013 UI.

## See also

[Beyond the basics: Lync 2013 SDK](beyond-the-basics-lync-2013-sdk.md)

