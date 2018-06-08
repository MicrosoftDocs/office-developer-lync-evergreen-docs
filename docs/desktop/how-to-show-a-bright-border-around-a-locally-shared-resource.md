---
title: 'How to: Show a bright border around a locally shared resource'
TOCTitle: 'How to: Show a bright border around a locally shared resource'
ms:assetid: d07626a9-aa8a-4331-8a60-17ec09d77020
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn391641(v=office.15)
ms:contentKeyID: 56293551
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Show a bright border around a locally shared resource

Learn about adding a UI hint such as a bright border around a process or desktop shared out by the Microsoft Lync 2013 API

**Last modified:** July 22, 2013

***Applies to:** Lync 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Code example: Example: ViewChrome.cs<br />
<br />
Prerequisites<br />
Declare class fields to support bright window border<br />
Showing a bright border around a shared screen<br />
Showing a bright border around a shared application window<br />
Handling move and resize events in the shared application<br />
Next steps<br />
Additional resources</p></td>
<td><p><img src="images/Dn391641.mod_icon_links_samples(Office.15).png" title="Related code snippets and sample apps" alt="Related code snippets and sample apps" /><br />
<a href="http://code.msdn.microsoft.com/displaying-a-highlighted-30039fd2">Displaying a highlighted border around a process window or desktop</a></p></td>
</tr>
</tbody>
</table>

**Show the user what is being shared:** A critical part of the application sharing experience is having confidence that you are sharing the application which you intend to share. Inadvertently sharing an application that shows inappropriate content for a conversation can have privacy or security related consequences. The Lync 2013 API lets you show a user the window title of a shareable application.

**Confirm the user’s choice:** Your application UI should let a user confirm that the application they have selected to share is the one they intended to share. Figure 1 shows a message box that shows the [SharingResource.Name](https://msdn.microsoft.com/en-us/library/jj274576\(v=office.15\)) property for the application that is selected by a user. After a user has confirmed their choice, application logic uses Lync 2013 API method calls to share the resource in the conversation.

Figure 1. Confirm resource to share.

  
![Application sharing confirmation dialog box](images/Dn391641.LyncClientSDK_ConfirmShareResource(Office.15).jpg "Application sharing confirmation dialog box")

**Show a UI hint:** Once the sharing confirmation is closed, you should show a very noticeable UI hint so the user is reminded that they are sharing a resource. Figure 1 shows a sample application that leaves the chosen shared application selected in a list. Don’t rely on a technique like this because selecting a resource doesn’t imply sharing it. The user may select a resource but not share it. An effective UI hint is one that clearly shows in the shared resource itself. For example, you can add a bright colored border around a shared window.

The Lync 2013 API does not have methods to create a bright border. Instead, use the Win32 API to make four calls into unmanaged code. Figure 2 shows a shared resource with a bright border as a clear UI hint that the spreadsheet is being shared in the conversation.

![Shared resource with gold border](images/Dn391641.LyncClientSDK_SharedResourceGoldBorder(Office.15).jpg "Shared resource with gold border")

## Prerequisites

The prerequisites for showing a UI hint in a resource sharing conversation are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

Understanding the following concepts is essential to using resource sharing conversions in an application.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Topic</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="how-to-start-a-lync-im-conversation.md">How to: Start a Lync IM conversation</a></p></td>
<td><p>Describes how to start a Lync 2013 conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-start-a-resource-sharing-conversation.md">How to: Start a resource sharing conversation</a></p></td>
<td><p>Learn how to use classes in Microsoft Lync 2013 SDK to select a locally shareable resource such as a desktop, monitor, or running program and share it in a Microsoft Lync 2013 conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="sharing-resources-in-a-conversation.md">Sharing resources in a conversation</a></p></td>
<td><p>Learn about programmatically sharing a computer monitor, desktop, or running program with another Microsoft Lync 2013 user in a conversation window by using classes in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="application-sharing-modality.md">Application sharing modality</a></p></td>
<td><p>Learn about the <strong>ApplicationSharingModality</strong> class and how it enables you to share resources in an application.</p></td>
</tr>
</tbody>
</table>

## Declare class fields to support bright window border

The following example declares the Win32 API methods that are called in the sample and supporting structures.

```csharp
        #region chrome form state
        public int borderWith = 5;
        public Chrome currentChrome;
        
        
        [DllImport("user32.dll")]
        private static extern int ShowWindow(IntPtr hWnd, uint Msg);

        [DllImport("user32.dll")]
        private static extern bool SetForegroundWindow(IntPtr hWnd);

        [DllImport("user32.dll")]
        [return: MarshalAs(UnmanagedType.Bool)]
        public static extern bool GetWindowRect(IntPtr hWnd, ref RECT lpRect);

        [DllImport("user32.dll")]
        private static extern bool GetWindowPlacement(IntPtr hWnd, out WINDOWPLACEMENT lpwndpl);
        private const UInt32 SW_MAXIMIZE = 3;

        private struct WINDOWPLACEMENT
        {
            public int length;
            public int flags;
            public int showCmd;
            public System.Drawing.Point ptMinPosition;
            public System.Drawing.Point ptMaxPosition;
            public System.Drawing.Rectangle rcNormalPosition;
        }
        [StructLayout(LayoutKind.Sequential)]
        public struct RECT
        {
            public int X;
            public int Y;
            public int Height;
            public int Width;

        }

        #endregion
```

## Showing a bright border around a shared screen

If the user has selected their desktop to share in a conversation, get all of the active screen objects and show a bright border around each screen.

Showing a bright border around a screen involves defining a rectangle of the same size and location as the screen desktop and then creating a bright-bordered chrome window that is shown as a border around the shared desktop.

### To show a border around a shared screen

1.  Get all active screens.
    
    ```csharp
                    System.Windows.Forms.Screen[] screens;
                    screens = Screen.AllScreens;
    ```

2.  Declare a Rectangle that is the same size and location as the shared screen
    
    ```csharp
                int x = screen.Bounds.X;
                int y = screen.Bounds.Y;
                Size size = screen.Bounds.Size;
                Rectangle desktop = new Rectangle(new Point(x, y), size);
    ```

3.  Create a new Windows Form in the dimensions of the desktop rectangle.
    
    The Chrome class is shown in the example section at the end of this topic.
    
    ```csharp
                Chrome chrome = new Chrome();
                chrome.Highlight(desktop, true, borderWith);
    ```

## Showing a bright border around a shared application window

To show a bright border around the selected application, you need to get the **Process** representing the shared application. The [SharingResource.Name](https://msdn.microsoft.com/en-us/library/jj274576\(v=office.15\)) property is the title of the main window of the selected process.

### To show a bright border around a shared application window

1.  Get the Process whose window title matches the user selection
    
    ```csharp
                Process[] processes = Process.GetProcesses();
                Process currentProcess = null;
                foreach (Process process in processes)
                {
                    if (selectedResourceObject.Name == process.MainWindowTitle)
                    {
                        currentProcess = process;
                        break;
    
                    }
                }
    ```

2.  Make sure the selected application is active and in the foreground.
    
    ```csharp
                //activate the selected application and bring to foreground
                IntPtr currentProcessHandle = currentProcess.MainWindowHandle;
                SetForegroundWindow(currentProcessHandle);
    ```

3.  Get the location and dimensions of the shared application.
    
    ```csharp
                //Get the location and rectangle of the selected application
                RECT processWindowSize = new RECT();
                GetWindowRect(currentProcessHandle, ref processWindowSize);
                Size size = new Size();
                size = new Size(processWindowSize.Height - processWindowSize.X, processWindowSize.Width - processWindowSize.Y);
                Rectangle processWindow = new Rectangle(new Point(processWindowSize.X, processWindowSize.Y), size);
                Rectangle currentProcessWindow = processWindow;
    ```

4.  Get the current visual state (restored, minimized, or maximized) of the shared application.
    
    ```csharp
                //Get the visual state of the shared application
                WINDOWPLACEMENT placement = new WINDOWPLACEMENT();
                placement.length = Marshal.SizeOf(placement);
                GetWindowPlacement(currentProcessHandle, out placement);
    ```

5.  Size the Chrome window based on the visual state of the shared application and then show the chrome.
    
    ```csharp
                //set the size of the Chrome window based on the visual state of the
                //shared application
                currentChrome = new Chrome();
                if (placement.showCmd == SW_MAXIMIZE)
                {
                    int taskBarSize = Screen.PrimaryScreen.Bounds.Height - Screen.PrimaryScreen.WorkingArea.Height;
                    processWindow.X = 0;
                    processWindow.Y = 0;
                    processWindow.Height = (processWindowSize.Width - borderWith * 2) + 2;
                    processWindow.Width = processWindowSize.Height + processWindowSize.X;
                    currentChrome.Highlight(processWindow, true, borderWith);
                }
                else
                {
                    currentChrome.Highlight(processWindow, false, borderWith);
                }
    ```

## Handling move and resize events in the shared application

The example class shown in this topic shows you the essentials of making a bright window border. The content in this topic will get you started, but you also need to code for movement and resizing events in the shared application itself. In other words, if the user drags the shared application on the desktop, your bright chrome border needs to move along with the shared application. The same is true with application resizing.

The [downloadable sample](http://code.msdn.microsoft.com/displaying-a-highlighted-30039fd2) that **ViewChrome** is taken from has event handling code for these move and resize events. If you want to use a bright border as a UI hint, you should download the sample to see how these event handlers are implemented.

## Example: ViewChrome.cs

The following example is a partial Windows Forms class that gives a Windows Forms application the ability to add a bright border around an application window that is shared by using the

```csharp
using Microsoft.Lync.Model.Conversation.Sharing;
using System;
using System.Diagnostics;
using System.Drawing;
using System.Runtime.InteropServices;
using System.Windows.Forms;
namespace ShareResources
{
    partial class ShareResources_Form
    {

        #region chrome form state
        public int borderWith = 5;
        public Chrome currentChrome;
        
        
        [DllImport("user32.dll")]
        private static extern int ShowWindow(IntPtr hWnd, uint Msg);

        [DllImport("user32.dll")]
        private static extern bool SetForegroundWindow(IntPtr hWnd);

        [DllImport("user32.dll")]
        [return: MarshalAs(UnmanagedType.Bool)]
        public static extern bool GetWindowRect(IntPtr hWnd, ref RECT lpRect);

        [DllImport("user32.dll")]
        private static extern bool GetWindowPlacement(IntPtr hWnd, out WINDOWPLACEMENT lpwndpl);
        private const UInt32 SW_MAXIMIZE = 3;

        private struct WINDOWPLACEMENT
        {
            public int length;
            public int flags;
            public int showCmd;
            public System.Drawing.Point ptMinPosition;
            public System.Drawing.Point ptMaxPosition;
            public System.Drawing.Rectangle rcNormalPosition;
        }
        [StructLayout(LayoutKind.Sequential)]
        public struct RECT
        {
            public int X;
            public int Y;
            public int Height;
            public int Width;

        }

        #endregion


        /// <summary>
        /// shows the shared resource "chrome" around the desktop
        /// </summary>
        /// <param name="screen"></param>
        private void ShowDesktopChrome(Screen screen)
        {
            int x = screen.Bounds.X;
            int y = screen.Bounds.Y;
            Size size = screen.Bounds.Size;
            Rectangle desktop = new Rectangle(new Point(x, y), size);
            Chrome chrome = new Chrome();
            chrome.Highlight(desktop, true, borderWith);

        }
        /// <summary>
        /// Shows the shared resouce "chrome" around the shared process
        /// </summary>
        /// <param name="selectedResourceObject"></param>
        private void ShowProcessChrome(SharingResource selectedResourceObject)
        {
            Process[] processes = Process.GetProcesses();
            Process currentProcess = null;
            foreach (Process process in processes)
            {
                if (selectedResourceObject.Name == process.MainWindowTitle)
                {
                    currentProcess = process;
                    break;

                }
            }

            IntPtr currentProcessHandle = currentProcess.MainWindowHandle;
            SetForegroundWindow(currentProcessHandle);
            RECT processWindowSize = new RECT();
            GetWindowRect(currentProcessHandle, ref processWindowSize);
            Size size = new Size();
            size = new Size(processWindowSize.Height - processWindowSize.X, processWindowSize.Width - processWindowSize.Y);
            Rectangle processWindow = new Rectangle(new Point(processWindowSize.X, processWindowSize.Y), size);
            Rectangle currentProcessWindow = processWindow;
            currentChrome = new Chrome();
            WINDOWPLACEMENT placement = new WINDOWPLACEMENT();
            placement.length = Marshal.SizeOf(placement);
            GetWindowPlacement(currentProcessHandle, out placement);

            if (placement.showCmd == SW_MAXIMIZE)
            {
                int taskBarSize = Screen.PrimaryScreen.Bounds.Height - Screen.PrimaryScreen.WorkingArea.Height;
                processWindow.X = 0;
                processWindow.Y = 0;
                processWindow.Height = (processWindowSize.Width - borderWith * 2) + 2;
                processWindow.Width = processWindowSize.Height + processWindowSize.X;
                currentChrome.Highlight(processWindow, true, borderWith);
            }
            else
            {
                currentChrome.Highlight(processWindow, false, borderWith);
            }
        }

        /// <summary>
        /// Closes the "chrome" winform that borders a shared resource
        /// </summary>
        private void CloseTheChrome()
        {
            if (currentChrome != null)
            {
                currentChrome.Close();
                currentChrome.Dispose();
            }
        }
    }
}
```

### The chrome window

The chrome window is a standard Windows Form whose border is modified to show a specified bright color and width. The content of the form is removed from inside of the border, leaving the form transparent except for the border itself.

```csharp
using System;
using System.Drawing;
using System.Windows.Forms;
using System.Runtime.InteropServices;
namespace ShareResources
{
    public partial class Chrome : Form
    {        
        private Rectangle innerRectangle;
        private Rectangle outerRectangle;
        private int BorderWidth = 5;        
        private Color fillColor = Color.Gold;
        private Color borderColor = Color.Navy;       
        [return: MarshalAs(UnmanagedType.Bool)]
        [DllImport("user32.dll")]
        public static extern bool SetWindowPos(IntPtr hWnd, IntPtr hWndInsertAfter, int X, int Y, int cX, int cY, uint uFlags);  

        public Chrome()
        {
            InitializeComponent();
            BackColor = fillColor;
            ForeColor = borderColor;
            base.FormBorderStyle = System.Windows.Forms.FormBorderStyle.None;
            base.MaximizeBox = false;
            base.MinimizeBox = false;
            base.ShowInTaskbar = false;
            base.StartPosition = FormStartPosition.Manual;            
            base.Text = "";
     
        }      

        public void Highlight(Rectangle rectangle, bool desktop,int borderWidth)
        {
            BorderWidth = borderWidth;
            SetLocation(rectangle, desktop);

            //Set as topmost window
            SetWindowPos(this.Handle, new IntPtr(-1), 0, 0, 0, 0, 0x43);
            Show();
        }

        public void SetLocation(Rectangle rectangle, bool desktop)
        {
            
            int width = BorderWidth;
            if (desktop)
            {
                this.TopMost = true;

                //Make the chrome window surface transparent

                //Define rectangle for chrome window border
                outerRectangle = new Rectangle(new Point(0, 0), rectangle.Size);
                //Define rectangle for chrome window content (everything inside of the window border)
                innerRectangle = new Rectangle(new Point(BorderWidth, BorderWidth), rectangle.Size - new Size(BorderWidth*2, BorderWidth*2));
                
                Region region = new Region(outerRectangle);
                //Exclude the contents of chrome window from region
                region.Exclude(innerRectangle);

                base.Location = rectangle.Location; 
                base.Size = outerRectangle.Size;
                base.Region = region;
            }
            else
            {
                this.TopMost = false;

                //Make the chrome window surface transparent
                //Define rectangle for chrome window border
                outerRectangle = new Rectangle(new Point(0, 0), rectangle.Size + new Size(width * 2, width * 2));
                //Define rectangle for chrome window content (everything inside of the window border)
                innerRectangle = new Rectangle(new Point(BorderWidth, BorderWidth), rectangle.Size);
                Region region = new Region(outerRectangle);
                //Exclude the contents of chrome window from region
                region.Exclude(innerRectangle);
                base.Location = rectangle.Location - new Size(width, width);
                base.Size = outerRectangle.Size;
                base.Region = region;
            }
        }

        protected override void OnPaint(PaintEventArgs e)
        {
            
            Rectangle rect = new Rectangle(outerRectangle.Left, outerRectangle.Top, outerRectangle.Width, outerRectangle.Height);
            Rectangle rectangle2 = new Rectangle(innerRectangle.Left , innerRectangle.Top , innerRectangle.Width, innerRectangle.Height );
            e.Graphics.DrawRectangle(new Pen(ForeColor), rectangle2);
            e.Graphics.DrawRectangle(new Pen(ForeColor), rect);
        }

        public void Show()
        {
            SetWindowPos(base.Handle, IntPtr.Zero, 0, 0, 0, 0, 0x53);
        }

    }
}
```

## Next steps

Now that you have created an application sharing feature in your application, you should learn about showing a sharing stage that gives users a view of applications shared by other conversation participants.

  - [How to: Add an application sharing view to your application](how-to-add-an-application-sharing-view-to-your-application.md)

## See also

  - [What you can do with desktop, application, and display sharing](what-you-can-do-with-desktop-application-and-display-sharing.md)

