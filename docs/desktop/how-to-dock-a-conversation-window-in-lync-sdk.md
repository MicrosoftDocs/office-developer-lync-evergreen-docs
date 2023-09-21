---
title: 'How to: Dock a conversation window in Lync SDK'
TOCTitle: 'How to: Dock a conversation window'
ms:assetid: 71b10f5a-32ee-458b-a157-7ea0212f798c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933086(v=office.15)
ms:contentKeyID: 50877217
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
- csharp
---

# How to: Dock a conversation window in Lync SDK

Learn how to dock a Microsoft Lync 2013 conversation window inside a WPF window and respond to conversation window sizing and attention events to prevent the conversation window from undocking when its size changes.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Declare a hosting window<br />
Initialize the hosting window<br />
Handle the window loaded event<br />
Dock a new conversation window<br />
Resize the docking control when conversation window size changes<br />
Code examples: Docking the conversation window sample<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for docking a conversation window are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

Before you can dock a conversation window, you must know how to start a conversation and get a reference to the resulting conversation window.

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
<td><p><a href="how-to-use-lync-controls-to-start-a-conversation.md">How to: Use Lync Controls to start a conversation</a></p></td>
<td><p>Describes how to use a Lync Control to start a new conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-start-an-automation-audio-conversation.md">How to: Start an automation audio conversation</a></p></td>
<td><p>Describes how to use Lync Automation to programmatically start a conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conversation-manager.md">Conversation manager</a></p></td>
<td><p>Describes how to use the <a href="https://msdn.microsoft.com/library/jj266018(v=office.15)">Microsoft.Lync.Model.Conversation.ConversationManager</a> class to start new conversations and listen for conversation invitations.</p></td>
</tr>
</tbody>
</table>

## Declare a hosting window

### To declare window controls

1.  Add a grid to the window and define three rows and three columns.
    
    ```xaml
            <Grid x:Uid="Grid_2">
                <Grid.RowDefinitions>
                    <RowDefinition x:Uid="RowDefinition_1" Height="Auto"/>
                    <RowDefinition x:Uid="RowDefinition_2" />
                    <RowDefinition x:Uid="RowDefinition_3" Height="50"/>
                </Grid.RowDefinitions>
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="81"/>
                    <ColumnDefinition x:Uid="ColDefinition_2"/>
                    <ColumnDefinition x:Uid="ColDefinition_3" Width="80"/>
                </Grid.ColumnDefinitions>
    
            </Grid>
    ```

2.  Add a stack panel to the first grid row, second column.
    
    The stack panel declares a location for the IM button and a text block that displays the name of the invited user.
    
    ```xaml
                <StackPanel 
                    x:Uid="StackPanel_1" 
                    Grid.Row="0" 
                    Grid.Column="1"
                    Orientation="Horizontal" 
                    HorizontalAlignment="Center" Margin="0,0">
                </StackPanel>
    ```

3.  Add a [Microsoft.Lync.Controls.StartInstantMessagingButton](https://msdn.microsoft.com/library/hh379340\(v=office.15\)) to the stack panel.
    
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/JJ933112.alert_note(Office.15).gif" title="Tip" alt="Tip" /><strong>Tip</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>The <strong>StartInstantMessagingButtonSource()</strong> property must be set to the SIP address of a Lync user. You can set it declaratively in XAML or in code by setting the property to a selected contact URI property from a contact search result as in the following example.</p>
    <p>SearchResult result = (SearchResult) _ContactSearchResultList.SelectedItem;<br />
    _myStartIMButton.Source = result.Contact.Uri;</p>
    <p></p></td>
    </tr>
    </tbody>
    </table>
    
    ```xaml
                    <Controls:StartInstantMessagingButton 
                        x:Uid="_myStartIMButton" 
                        Grid.Row="0" 
                        x:Name="_myStartIMButton" 
                        />
    ```

4.  Add a text box in the stack panel that displays the name of the person to invite.
    
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>The text block is bound to the <strong>StartInstantMessagingButtonDisplayName()</strong> property.</p></td>
    </tr>
    </tbody>
    </table>
    
    ```xaml
                    <TextBlock x:Uid="TextBlock_1" Text="{Binding ElementName=_myStartIMButton, 
                        Path=DisplayName}"/>
    ```

5.  Add a WindowsFormsHost control to the grid in the second row, second column.
    
    ```xaml
                <WindowsFormsHost 
                    x:Uid="_windowsFormsHost" 
                    x:Name="_windowsFormsHost" 
                    Grid.Row="1" 
                    Grid.Column="1"
    
                    VerticalAlignment="Stretch" 
                    HorizontalAlignment="Stretch" Margin="0,5,0,45" Grid.RowSpan="2">
    
                </WindowsFormsHost>
    ```

6.  Add a panel to the WindowsFormsHost control.
    
    This panel provides the scrolling feature of the sample.
    
    ```xaml
                            <wf:Panel 
                                x:Uid="_scrollViewer"
                                x:Name="_scrollViewer"
                                AutoScroll="True"
    Visible="False" />
    ```

The WPF window that is declared in this sample contains a multi-row, column grid that structures the controls in the window. Other controls include a stack panel to align a StartInstantMessagingButton control and string, a WindowsFormsHost control to accept a docked Lync 2013 conversation window, and a set of nested panels that allow the window to contain the conversation window regardless of its dimensions. The following figure shows two dialog boxes. The dialog box on the left is the WPF window that is declared in this sample. The dialog box on the right is a Lync 2013 conversation window that is not docked.

  
![Side by side view of a docked conversation window](images/JJ933086.LyncClientSDK_ConversationWindowDocking(Office.15).jpg "Side by side view of a docked conversation window")

## Initialize the hosting window

This procedure constructs the conversation manager wrapper class and registers for conversation-related events on the active conversation window.

### To register for events

1.  Register for the **FrameworkElement.Loaded** and **FrameworkElement.Unloaded** events.
    
    ```csharp
                Loaded += HandleLoaded;
                Unloaded += HandleUnloaded;
    ```

2.  Construct the view model class that encapsulates the [Microsoft.Lync.Model.Conversation.ConversationManager](https://msdn.microsoft.com/library/jj266018\(v=office.15\)) and [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) objects.
    
    ```csharp
                _dockingConversationVm = new DockingConversationViewModel();
    ```

3.  Register for events on the [Microsoft.Lync.Model.Conversation.ConversationManager](https://msdn.microsoft.com/library/jj266018\(v=office.15\)) object.
    
    The following example is taken from the sample Conversation manager model class and runs in the constructor that is called in the previous step.
    
    ```csharp
                //Subscribe to the Lync ConversationManager's ConversationAdded and ConversationRemoved events
                _lync.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;
                _lync.ConversationManager.ConversationRemoved += ConversationManager_ConversationRemoved;
    ```

4.  Create the helper WindowFlash class that flashes the WPF window when the conversation window needs attention.
    
    ```csharp
                _windowFlash = new WindowFlash(this, false);
                
    ```

5.  Register for the **Activated** event on the window so that you're notified that the window has the focus and flashing can stop.
    
    ```csharp
    Activated += MainWindowActivated;
    ```

## Handle the window loaded event

When the window is loaded, a panel is created to nest in the scrollable panel that we declared in the XAML and then the handle to the new panel to the **StartInstantMessagingButton** is provided so that when a conversation window is opened, it's automatically docked inside the panel.

### To handle the window loaded event

1.  Create a method whose signature matches the callback event signature of the **FrameworkElement.Loaded** event.
    
    ``` 
            /// <summary>
            /// This method handles the Main Window Loaded Event. It gets fired when the window is loaded.
            /// </summary>
            void HandleLoaded(object sender, RoutedEventArgs e)
            {
            }
    ```

2.  Create a new panel control in the event handler.
    
    ```csharp
                // Create the host for the conversation window.
                _conversationWindowParentPanel = new Panel();
    ```

3.  Add the new panel to the scroll viewing panel.
    
    ```csharp
                _scrollViewer.Controls.Add(_conversationWindowParentPanel);
    ```

4.  Get the handle to the new panel and set it as context for all new conversations created by the **StartInstantMessagingButton**.
    
    When the [ConversationContextualInfo.ParentWindowHandle](https://msdn.microsoft.com/library/hh379561\(v=office.15\)) property is set on the control, any conversation started by clicking the control is docked in the container control whose handle is set as context.
    
    ``` 
                // Get the handle of the panel where we'll dock the conversation:
                IntPtr handle = _conversationWindowParentPanel.Handle;
    
                // Tell the StartInstantMessagingButton to dock the conversation into the panel we created above:
                _myStartIMButton.ContextualInformation = new ConversationContextualInfo{ParentWindowHandle = handle};
    ```

5.  Set the **StartInstantMessagingButtonSource()** property to the SIP address of a Lync user.
    
    When the button is clicked by the user, a conversation with the user specified by the address is started.
    
    ```csharp
                //Set the source of the IM button to a SIP address
                _myStartIMButton.Source = "dani@contoso.com";
    ```

6.  Register for the **FrameworkElement.SizeChanged** event so that there is a response when a user changes the size of the WPF window.
    
    ```csharp
                // Subscribe to the MainWindow.SizeChanged event so we can redock the conversation when layout changes happen.
                SizeChanged += HandleWindowSizeChanged;
    ```

## Dock a new conversation window

When a user clicks the **StartInstantMessagingButton** button, Lync 2013 opens a new conversation window and the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event is raised. The handle to the docking panel was added as context on the **StartInstantMessagingButton** when the new panel was created. When this context is set, any conversation window that is opened by the button is automatically docked in the container control.

The sample uses this event to obtain an [Microsoft.Lync.Model.Extensibility.ConversationWindow](https://msdn.microsoft.com/library/jj293606\(v=office.15\)) object that represents the new conversation window by calling the [Automation.GetConversationWindow](https://msdn.microsoft.com/library/jj267667\(v=office.15\)) method. To respond to size change or attention events, the sample registers for the two events described in Resize the docking control when conversation window size changes.

```csharp
        /// <summary>
        /// This event is fired when the Conversation is created.  We use the automation
        /// API to get the ConversationWindow for the Conversation, and subscribe to important window events.”
        /// </summary>
        void ConversationManager_ConversationAdded(object sender, ConversationManagerEventArgs e)
        {
            if (ConversationAddedEvent != null)
            {
                _conversation = e.Conversation;
                try
                {
                    Automation automation = LyncClient.GetAutomation();
                    _conversationWindow = automation.GetConversationWindow(_conversation);
                }
                catch (LyncClientException lyncClientException)
                {
                    Console.WriteLine(lyncClientException);
                }

                if (_conversationWindow != null)
                {
                    //Subscribe to ConversationWindows's NeedsAttention and NeedsSizeChanged events
                    _conversationWindow.NeedsAttention += HandleNeedsAttention;
                    _conversationWindow.NeedsSizeChange += HandleNeedsSizeChange;
                    ConversationAddedEvent(this, null);
                }
            }
        }
```

## Resize the docking control when conversation window size changes

The **Conversation** window object is encapsulated by the Conversation manager model class and raises the two events as follows:

  - Conversation window size changed

  - Conversation window needs attention

### Handle the conversation window size changed event

A conversation window size change occurs when a visual element is added to the conversation window. For example, a user adds video to the conversation and a video window control is opened in the conversation window.

The sample application uses a pair of nested panel controls to contain the conversation window. The outer panel implements scroll bars so that if the inner panel is resized beyond the design time dimensions, scroll bars are shown on the outer panel. This allows the WPF window dimensions to remain fixed without regard to the dimensions of the docked conversation window.

If the dimensions of the scrolling panel are larger than the minimum dimensions of the conversation window, this event handler sets the dimensions of the docking panel to those of the scrolling panel. This logic is complex because of one or both scroll bars on the scrolling panel. Scroll bars reduce the display area of the panel and the logic must calculate the size of the scrolling panel with scroll bars and determine whether these dimensions are larger than the minimum size of the conversation window. If they are not, the docking panel dimensions are set to the minimum dimensions of the conversation window and scroll bars are displayed. Finally, the conversation window is redocked in the docking panel and resized to the dimensions of the docking panel.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>You must respond to this event within 5 seconds by resizing the docking panel to fit the new dimensions of the conversation window. Failure to resize the docking panel causes the conversation window to undock.</p></td>
</tr>
</tbody>
</table>

### To handle the conversation window size changed event

1.  Get the new minimum dimensions of the conversation window.
    
    The following example handles the **ConversationWindowNeedsSizeChangedEvent** exposed by the helper Conversation manager model class. The helper class handles the [ConversationWindow.NeedsSizeChange](https://msdn.microsoft.com/library/jj277925\(v=office.15\)) event. The example reads the **MinSize** property on the helper class that returns a **Size** object for the new minimum size of the conversation window.
    
    ```csharp
                int minWidth = _dockingConversationVm.MinSize.Width;
                int minHeight = _dockingConversationVm.MinSize.Height;
    ```

2.  Get the display area dimensions of the scrolling panel, excluding the width of horizontal and vertical scroll bars.
    
    ```csharp
                int availWidthWithScrollbar = _scrollViewer.Size.Width - SystemInformation.VerticalScrollBarWidth;
                int availableHeightWithScrollbar = _scrollViewer.Size.Height - SystemInformation.HorizontalScrollBarHeight;
    ```

3.  Determine whether setting the docking panel to the new minimum size of the conversation window requires the parent scrolling panel scroll bars to display.
    
    Displaying the scroll bar for one dimension shortens the other display dimension. For this reason, the new dimensions of the docking panel must be adapted to the display area of the scrolling panel with one or both scroll bars visible.
    
    ```csharp
                bool NeedsHorizontalScrollbars = _scrollViewer.Size.Width < minWidth;
                bool NeedsVerticalScrollbars = _scrollViewer.Size.Height < minHeight;
    
                if (NeedsHorizontalScrollbars ^ NeedsVerticalScrollbars)
                {
                    // If only one scrollbar is visible, check to see whether or not the addition
                    // of this scrollbar forces the other scrollbar to become visible...
                    if (NeedsVerticalScrollbars)
                    {
                        NeedsHorizontalScrollbars = availWidthWithScrollbar < minWidth;
                    }
                    else
                    {
                        NeedsVerticalScrollbars = availableHeightWithScrollbar < minHeight;
                    }
                }
    ```

4.  Set the dimensions of the docking panel to the larger of the minimum conversation window dimensions or the scrolling panel dimensions.
    
    ```csharp
                int width = NeedsHorizontalScrollbars
                    ? minWidth : (NeedsVerticalScrollbars ? availWidthWithScrollbar : _scrollViewer.Size.Width);
                int height = NeedsVerticalScrollbars
                    ? minHeight : (NeedsHorizontalScrollbars ? availableHeightWithScrollbar : _scrollViewer.Size.Height);
    
                //the panel is the actual container control and must be re-sized when the conversation window size changes
                //or the user resizes the scrollviewer.
                _conversationWindowParentPanel.Size = new Size(width, height);
                _conversationWindowParentPanel.Invoke(
                     (Action<IntPtr>)_dockingConversationVm.RedockConversation,
                    _conversationWindowParentPanel.Handle);
    ```

5.  Redock the conversation window in the resized docking panel.
    
    The following example docks the conversation window by calling the **RedockConversation** method from the model view class by calling the [ConversationWindow.Dock](https://msdn.microsoft.com/library/jj294013\(v=office.15\)) method.
    
    ```csharp
            /// <summary>
            /// This method redocks the conversation window. When the docked conversation window adds a new visual
            /// element(such as video, a participant list, desktop sharing e.t.c) it's size changes. To accommodate
            /// this new element the conversation window will increase/decrease it's size accordingly. During this
            /// process we'll have to redock the newly changed window into the parent window. panelHandle is the
            /// Handle property of the parent window where docking will occur.
            /// </summary>
            public void RedockConversation(IntPtr panelHandle)
            {
                if (_conversationWindow == null)
                {
                    return;
                }
                try
                {
                    _conversationWindow.Dock(panelHandle);
                }
                catch (LyncClientException lyncClientException)
                {
                    Console.WriteLine(lyncClientException);
                }
            }
    ```

### Handle the conversation window needs attention event

If the application window does not have focus when the docked conversation window needs attention because of an event like a new IM message is received, then the application window should flash to get a user’s attention.

The sample makes a call into a method exposed by the unmanaged user32.dll. **FlashWindow** takes the handle of the window to flash and a Boolean value that indicates whether to flash. The call is made on a timer that ticks every half second. To see how the sample flashes the WPF window, see the WindowFlash class section.

## Code examples: Docking the conversation window sample

The sample application from which the previous code examples are taken is provide in this section. This is a WPF application that is built on the view, view model, model (MVVM) design. The sample contains an XAML declaration file, a C\# code-behind file that sets properties on elements declared in the XAML file, and a C\# file that encapsulates the conversation manager and handles events raised by the conversation manager and conversation window. Where appropriate, the class exposes event delegates to the view model logic.

### XAML declaration

The following example declares a window that will contain a docked conversation window.

```xaml
    
<Window x:Uid="Window_1" x:Class="DockingConversationWindowSample.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:Controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
        xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
        Title="Contoso Internal Chat Window" Height="548" Width="811" Closing="Window_Closing_2"  >
    <Grid x:Uid="Grid_1">
        <Grid x:Uid="Grid_2">
            <Grid.RowDefinitions>
                <RowDefinition x:Uid="RowDefinition_1" Height="Auto"/>
                <RowDefinition x:Uid="RowDefinition_2" />
                <RowDefinition x:Uid="RowDefinition_3" Height="50"/>
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="81"/>
                <ColumnDefinition x:Uid="ColDefinition_2"/>
                <ColumnDefinition x:Uid="ColDefinition_3" Width="80"/>
            </Grid.ColumnDefinitions>
            <StackPanel 
                x:Uid="StackPanel_1" 
                Grid.Row="0" 
                Grid.Column="1"
                Orientation="Horizontal" 
                HorizontalAlignment="Center" Margin="0,0">
                <Controls:StartInstantMessagingButton 
                    x:Uid="_myStartIMButton" 
                    Grid.Row="0" 
                    x:Name="_myStartIMButton" 
                    Source="sip:davidj@contoso.com"
                    />
                <TextBlock x:Uid="TextBlock_1" Text="{Binding ElementName=_myStartIMButton, 
                    Path=DisplayName}"/>
            </StackPanel>
            <WindowsFormsHost 
                x:Uid="_windowsFormsHost" 
                x:Name="_windowsFormsHost" 
                Grid.Row="1" 
                Grid.Column="1"

                VerticalAlignment="Stretch" 
                HorizontalAlignment="Stretch" Margin="0,5,0,45" Grid.RowSpan="2">
                        <wf:Panel 
                            x:Uid="_scrollViewer"
                            x:Name="_scrollViewer"
                            AutoScroll="True"
                            />
            </WindowsFormsHost>
            <Button Content="End Conversation" Width="100" Grid.Column="1" 
                    Grid.Row="3" Height="30" Click="Button_Click_2" />
            <Label Grid.Column="0" HorizontalAlignment="Center" Margin="10,10,10,10" 
                   Grid.Row="2" VerticalAlignment="Center" Width="635">
            </Label>
        </Grid>
    </Grid>
</Window>
```

### View code-behind logic

The following logic animates the previously declared view.

```csharp
using System;
using System.Diagnostics;
using System.Windows;
using System.Windows.Forms;
using Microsoft.Lync.Controls;
using Panel = System.Windows.Forms.Panel;
using Size = System.Drawing.Size;

namespace DockingConversationWindowSample
{
    /// <summary>
    /// This class provides the interaction logic for a WPF window into which we
    /// will dock a Lync ConversationWindow.
    /// </summary>
    public partial class MainWindow
    {

        #region Fields

        private readonly DockingConversationViewModel _dockingConversationVm;
        private Panel _conversationWindowParentPanel;
        private readonly WindowFlash _windowFlash;
        private IntPtr _PanelHandle;
       

        #endregion

        #region Constructor

        /// <summary>
        /// The class constructor instantiates _dockingConversationVm and subscribes to it's events.
        /// It also creates and instance of WindowFlash and subscribes to the main window Activated event.
        /// </summary>
        public MainWindow()
        {
            InitializeComponent();
            Loaded += HandleLoaded;
            Unloaded += HandleUnloaded;
            _dockingConversationVm = new DockingConversationViewModel();
            _dockingConversationVm.ConversationAddedEvent += HandleModelConversationAddedEvent;
            _dockingConversationVm.ConversationRemoveEvent += HandleModelConversationRemoveEvent;
            _dockingConversationVm.ConversationWindowNeedsAttentionEvent += HandleModelConversationWindowNeedsAttentionEvent;
            _dockingConversationVm.ConversationWindowNeedsSizeChangedEvent += HandleModelConversationWindowNeedsSizeChangedEvent;

            _windowFlash = new WindowFlash(this, false);
            Activated += MainWindowActivated;

        }

        #endregion

        #region Window Event Handlers

        /// <summary>
        /// When the MainWindow changes in size, we must resize the _conversationWindowParentPanel,
        /// and redock the ConversationWindow to it.
        /// </summary>
        void HandleWindowSizeChanged(object sender, EventArgs eventArgs)
        {
            Debug.WriteLine("FrameworkElement.SizeChanged - HandleWindowSizeChanged");

            _conversationWindowParentPanel.Invoke((Action)ResizeConversation);
        }

        /// <summary>
        /// This method handles the Main Window Loaded Event. It gets fired when the window is loaded.
        /// </summary>
        void HandleLoaded(object sender, RoutedEventArgs e)
        {
            // Create the host for the conversation window.
            _conversationWindowParentPanel = new Panel();
            _PanelHandle = _conversationWindowParentPanel.Handle;
            // We are using 2 layers of WindowsForms panels to achieve a scrolling effect.  The inner layer (_conversationWindowParentPanel)
            // is the direct ancestor of the conversation window, and the size of this panel determines the size of the ConversationWindow 
            // when we invoke Dock().  Therefore, we want to retain control over the sizing of this panel to insure that it can always be 
            // at least as big as the MinimumSize required by the ConversationWindow, as dictated in the NeedsSizeChange event.
            // The outer layer (_scrollViewer) is used to accommodate the _conversationWindowParentPanel when it's too large for the 
            // application. This panel is set to scroll automatically, or turn the scrollbars off when they are not needed. Because of the
            // automatic sizing and scrolling behavior, we cannot host the ConversationWindow directly in this panel, since it does not 
            // guarantee our minimum size requirements.
            _scrollViewer.Controls.Add(_conversationWindowParentPanel);

            // Get the handle of the panel where we'll dock the conversation:
            IntPtr handle = _conversationWindowParentPanel.Handle;

            // Tell the StartInstantMessagingButton to dock the conversation into the panel we created above:
            _myStartIMButton.ContextualInformation = new ConversationContextualInfo{ParentWindowHandle = handle};

            //Set the source of the IM button to a SIP address
            _myStartIMButton.Source = "dani@contoso.com";

            // Subscribe to the MainWindow.SizeChanged event so we can redock the conversation when layout changes happen.
            SizeChanged += HandleWindowSizeChanged;
        }

        private void HandleUnloaded(object sender, RoutedEventArgs e)
        {
            _dockingConversationVm.Unregister();
        }

        /// <summary>
        /// Event fired when Main Window is activated. 
        /// This method is used to stop flashing the window.
        /// </summary>
        void MainWindowActivated(object sender, EventArgs e)
        {
            _windowFlash.StopFlashing();
        }

        #endregion

        #region Model Event Handlers

        /// <summary>
        /// This method handles the ConversationWindow's NeedSizeChanged event. 
        /// </summary>
        void HandleModelConversationWindowNeedsSizeChangedEvent(object sender, EventArgs eventArgs)
        {
            // The conversation window events do not fire on the UI thread, so we use the Invoke method to handle them.
            _conversationWindowParentPanel.Invoke((Action)ResizeConversation);

        }

        /// <summary>
        /// this method handles the ConversationWindow's NeedsAttention event
        /// </summary>
        void HandleModelConversationWindowNeedsAttentionEvent(object sender, EventArgs eventArgs)
        {
            _conversationWindowParentPanel.Invoke((Action)FlashWhenInactive);
        }

        /// <summary>
        /// Handler for the Conversation Added event
        /// </summary>
        private void HandleModelConversationAddedEvent(object sender, EventArgs eventArgs)
        {
            Debug.WriteLine("HandleModelNewConversationEvent");

            // Dock the new conversation window in the window
            _conversationWindowParentPanel.Invoke((Action)ResizeConversation);
        }

        /// <summary>
        /// Handler for the Conversation Removed event
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="eventArgs"></param>
        static void HandleModelConversationRemoveEvent(object sender, EventArgs eventArgs)
        {
            Debug.WriteLine("HandleModelConversationRemoveEvent");
        }

        #endregion

        #region Private Methods

        /// <summary>
        /// Helper method to Resize the conversation window.
        /// When the MainWindow size is changed, or the ConversationWindow changes size, we must adjust our layout.
        /// This method determines whether or not scrollbars will be needed (they are added automatically by _scrollViewer panel if needed).
        /// Then, based on this information, it manually sets the size of the _conversationWindowParentPanel to a new dimension
        /// which will be at least as big as the MinimumSize required by the ConversationWindow, but bigger if more space is available.
        /// The size is then adjusted down when one scrollbar has been added to insure that the window fits perfectly in the remaining space
        /// </summary>
        private void ResizeConversation()
        {

            int minWidth = _dockingConversationVm.MinSize.Width;
            int minHeight = _dockingConversationVm.MinSize.Height;
            int availWidthWithScrollbar = _scrollViewer.Size.Width - SystemInformation.VerticalScrollBarWidth;
            int availableHeightWithScrollbar = _scrollViewer.Size.Height - SystemInformation.HorizontalScrollBarHeight;

            Debug.WriteLine(GetTime() + 
                " ResizeConversation: Min HW " + 
                minHeight.ToString() + 
                "/" + 
                minWidth.ToString());

            Debug.WriteLine(GetTime() + 
                " Current scroll viewer size: HW " + 
                _scrollViewer.Size.Height.ToString() + 
                "/" + 
                _scrollViewer.Size.Width.ToString());

            Debug.WriteLine(GetTime() + 
                " Current panel size: HW " + 
                _conversationWindowParentPanel.Size.Height.ToString() + 
                "/" + 
                _conversationWindowParentPanel.Size.Width.ToString());

            //The scrollViewer is the container for the panel + the related scroll bars. 
            //The dimensions of the scrollViewer can only be changed by the user when they
            //drag the window in or out.  The scroll viewer dimensions can be smaller than the 
            //conversation window. In this case, the scroll bars appear.
            //if the panel is large enough to hold the complete conversation window, the scroll
            //bars disappear and the scrollviewer has the same dimension as the panel.
            bool NeedsHorizontalScrollbars = _scrollViewer.Size.Width < minWidth;
            bool NeedsVerticalScrollbars = _scrollViewer.Size.Height < minHeight;

            if (NeedsHorizontalScrollbars ^ NeedsVerticalScrollbars)
            {
                // If only one scrollbar is visible, check to see whether or not the addition
                // of this scrollbar forces the other scrollbar to become visible...
                if (NeedsVerticalScrollbars)
                {
                    NeedsHorizontalScrollbars = availWidthWithScrollbar < minWidth;
                }
                else
                {
                    NeedsVerticalScrollbars = availableHeightWithScrollbar < minHeight;
                }
            }

            //If the width of the scrolling panel is still greater than the minimum width required,
            //set the width of the docking panel to the display area width of the scrolling panel
            //If the height of the scrolling panel is still greater than the minimum height required,
            //set the height of the docking panel to the display area height of the scrolling panel
            int width = NeedsHorizontalScrollbars
                ? minWidth : (NeedsVerticalScrollbars ? availWidthWithScrollbar : _scrollViewer.Size.Width);
            int height = NeedsVerticalScrollbars
                ? minHeight : (NeedsHorizontalScrollbars ? availableHeightWithScrollbar : _scrollViewer.Size.Height);

            //the panel is the actual container control and must be resized when the conversation window size changes
            //or the user resizes the scrollviewer.
            _conversationWindowParentPanel.Size = new Size(width, height);
            _conversationWindowParentPanel.Invoke((Action<IntPtr>)_dockingConversationVm.RedockConversation, _conversationWindowParentPanel.Handle);

            Debug.WriteLine(GetTime() + 
                " New scroll viewer size: HW " +
                _scrollViewer.Size.Height.ToString() + 
                "/" + 
                _scrollViewer.Size.Width.ToString());

            Debug.WriteLine(GetTime() + 
                " New panel size: HW " +
                _conversationWindowParentPanel.Size.Height.ToString() +
                "/" + 
                _conversationWindowParentPanel.Size.Width.ToString());
        }

        /// <summary>
        /// Returns the current time to the millisecond as a string
        /// </summary>
        /// <returns></returns>
        private string GetTime()
        {
            return System.DateTime.Now.Hour.ToString() + 
                " " +  
                System.DateTime.Now.Minute.ToString() + 
                ":" + 
                System.DateTime.Now.Second.ToString() + 
                "." +
                System.DateTime.Now.Millisecond.ToString();
        }

        /// <summary>
        /// Helper method to set the window flashing
        /// </summary>
        private void FlashWhenInactive()
        {
            if (IsFocused || IsActive)
            {
                _windowFlash.StopFlashing();
            }
            else
            {
                _windowFlash.StartFlashing();
            }
        }

        #endregion

        private void Button_Click_2(object sender, RoutedEventArgs e)
        {
            _dockingConversationVm.EndTheConversation();
            _conversationWindowParentPanel.Size = _scrollViewer.Size;
        }

        private void Window_Closing_2(object sender, System.ComponentModel.CancelEventArgs e)
        {
            _dockingConversationVm.EndTheConversation();

        }

        private void ContactSearchResultList_SelectionChanged(object sender, System.Windows.Controls.SelectionChangedEventArgs e)
        {
            Microsoft.Lync.Controls.ContactSearchResultList _ContactSearchResultList = (Microsoft.Lync.Controls.ContactSearchResultList)sender;
            SearchResult result = (SearchResult)_ContactSearchResultList.SelectedItem;
            _myStartIMButton.Source = result.Contact.Uri;
            
        }
    }
}
```

### Conversation manager model class

The following example encapsulates the conversation manager and handles events for the conversation manager and conversation window.

```csharp
using System;
using System.Drawing;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Conversation;
using Microsoft.Lync.Model.Extensibility;
using System.Diagnostics;

namespace DockingConversationWindowSample
{
    /// <summary>
    /// This class encapsulates the behavior of Lync, and exposes data and
    /// events about a conversation to the View.
    /// </summary>
    class DockingConversationViewModel
    {
        #region Events

        public event EventHandler ConversationWindowNeedsAttentionEvent;
        public event EventHandler ConversationWindowNeedsSizeChangedEvent;
        public event EventHandler ConversationRemoveEvent;
        public event EventHandler ConversationAddedEvent;

        #endregion

        #region Fields

        private ConversationWindow _conversationWindow;
        private Conversation _conversation;
        private LyncClient _lync;

        #endregion

        #region Properties

        public Size MinSize
        {
            get;
            private set;
        }

        public Size MaxSize
        {
            get;
            private set;
        }

        public Size RecommendedSize
        {
            get;
            private set;
        }

        #endregion

        #region Constructor

        /// <summary>
        /// The class constructor creates an instance of LyncClient and subscribes to the 
        /// ConversationManager's ConversationAdded and ConversationRemoved events.
        /// </summary>
        /// <exception cref="Exception">Lync is not signed in</exception>
        public DockingConversationViewModel()
        {
            try
            {
                _lync = LyncClient.GetClient();
            }
            catch (ClientNotFoundException clientNotFoundException)
            {
                Console.Out.WriteLine(clientNotFoundException);
                return;
            }
            catch (NotStartedByUserException notStartedByUserException)
            {
                Console.Out.WriteLine(notStartedByUserException);
                return;
            }
            catch (LyncClientException lyncClientException)
            {
                Console.Out.WriteLine(lyncClientException);
                return;
            }
            catch (SystemException systemException)
            {
                if (IsLyncException(systemException))
                {
                    // Log the exception thrown by the Lync Model API.
                    Console.WriteLine("Error: " + systemException);
                    return;
                }
                else
                {
                    // Rethrow the SystemException which did not come from the Lync Model API.
                    throw;
                }
            }

            if (_lync.State != ClientState.SignedIn)
            {
                Console.WriteLine("Not signed in");
            }

            //Subscribe to the Lync ConversationManager's ConversationAdded and ConversationRemoved events
            _lync.ConversationManager.ConversationAdded += HandleConversationAdded;
            _lync.ConversationManager.ConversationRemoved += HandleConversationRemoved;
        }

        #endregion

        #region Public Methods

        /// <summary>
        /// This method redocks the conversation window. When the docked conversation window adds a new visual
        /// element(such as video, a participant list, desktop sharing e.t.c) it's size changes. To accommodate
        /// this new element the conversation window will increase/decrease it's size accordingly. During this
        /// process we'll have to redock the newly changed window into the parent window. panelHandle is the
        /// Handle property of the parent window where docking will occur.
        /// </summary>
        public void RedockConversation(IntPtr panelHandle)
        {
            if (_conversationWindow != null && _conversationWindow.IsDocked)
            {
                try
                {
                    _conversationWindow.Dock(panelHandle);
                }
                catch (LyncClientException lyncClientException)
                {
                    Console.WriteLine(lyncClientException);
                }
                catch (SystemException systemException)
                {
                    if (IsLyncException(systemException))
                    {
                        // Log the exception thrown by the Lync Model API.
                        Console.WriteLine("Error: " + systemException);
                    }
                    else
                    {
                        // Rethrow the SystemException which did not come from the Lync Model API.
                        throw;
                    }
                }

            }
        }

        public void Unregister()
        {
            if (_lync != null)
            {
                _lync.ConversationManager.ConversationAdded -= HandleConversationAdded;
                _lync.ConversationManager.ConversationRemoved -= HandleConversationRemoved;
            }
            if (_conversationWindow != null)
            {
                _conversationWindow.NeedsAttention -= HandleNeedsAttention;
                _conversationWindow.NeedsSizeChange -= HandleNeedsSizeChange;
            }
        }

        public void EndTheConversation()
        {
            if (_conversation != null && _conversation.State != ConversationState.Terminated)
            {
                _conversation.End();
            }
        }

        #endregion

        #region ConversationWindow events

        /// <summary>
        /// The ConversationWindow.NeedsSizeChanged event fires when the docked conversation window has added a new
        /// visual element (such as video, a participant list, and desktop sharing), and if it were not docked, the
        /// window would have automatically grown in size to accommodate this new element. We must respond to this 
        /// event within 5 seconds by increasing the size of the conversation windows first direct ancestor (the 
        /// ParentWindow handle to which it's docked). Max, min, and recommended size information for the 
        /// ConversationWindow is made available in this event, and cannot be accessed outside the event, so we 
        /// capture it here before propagating the event to our MainWindow where the containing panel can be adjusted.
        /// </summary>
        void HandleNeedsSizeChange(object sender, ConversationWindowNeedsSizeChangeEventArgs e)
        {

            MinSize = new Size(e.MinimumWindowWidth, e.MinimumWindowHeight);

            var conversationWindow = sender as ConversationWindow;
            if (ConversationWindowNeedsSizeChangedEvent != null && conversationWindow != null)
            {
                ConversationWindowNeedsSizeChangedEvent(this, null);
            }

        }

        /// <summary>
        /// The ConversationWindow.NeedsAttention event fires when a new message or other conversation
        /// element has been delivered (such as an incoming IM) but the window does not have focus.
        /// Lync handles this situation by causing the title bar of the window to flash until the user clicks on the
        /// window to acknowledge the new information.  we'll propagate this event to the MainWindow
        /// where a similar behavior can be simulated.
        /// </summary>
        void HandleNeedsAttention(object sender, ConversationWindowNeedsAttentionEventArgs e)
        {
            if (ConversationWindowNeedsAttentionEvent != null)
            {
                ConversationWindowNeedsAttentionEvent(this, null);
            }
        }

        #endregion

        #region ConversationManager events

        /// <summary>
        /// This event is fired when the ConversationWindow is closing.  This sample application is handling
        /// the event for illustration purposes only.
        /// </summary>
        void HandleConversationRemoved(object sender, ConversationManagerEventArgs e)
        {
            if (ConversationRemoveEvent != null)
            {
                ConversationRemoveEvent(this, null);
            }
        }

        /// <summary>
        /// This event is fired when the Conversation is created.  We use the automation
        /// API to get the ConversationWindow for the Conversation, and subscribe to important window events.”
        /// </summary>
        void HandleConversationAdded(object sender, ConversationManagerEventArgs e)
        {
            if (ConversationAddedEvent != null)
            {
                _conversation = e.Conversation;
                try
                {
                    Automation automation = LyncClient.GetAutomation();
                    _conversationWindow = automation.GetConversationWindow(_conversation);
                }
                catch (LyncClientException lyncClientException)
                {
                    Console.WriteLine(lyncClientException);
                }
                catch (SystemException systemException)
                {
                    if (IsLyncException(systemException))
                    {
                        // Log the exception thrown by the Lync Model API.
                        Console.WriteLine("Error: " + systemException);
                    }
                    else
                    {
                        // Rethrow the SystemException which did not come from the Lync Model API.
                        throw;
                    }
                }

                if (_conversationWindow != null)
                {
                    //Subscribe to ConversationWindows's NeedsAttention and NeedsSizeChanged events
                    _conversationWindow.NeedsAttention += HandleNeedsAttention;
                    _conversationWindow.NeedsSizeChange += HandleNeedsSizeChange;
                    ConversationAddedEvent(this, null);
                }
            }
        }

        #endregion

        #region Private Methods

        /// <summary>
        /// Identify if a particular SystemException is one of the exceptions which may be thrown
        /// by the Lync Model API.
        /// </summary>
        /// <param name="ex"></param>
        /// <returns></returns>
        private bool IsLyncException(SystemException ex)
        {
            return
                ex is NotImplementedException ||
                ex is ArgumentException ||
                ex is NullReferenceException ||
                ex is NotSupportedException ||
                ex is ArgumentOutOfRangeException ||
                ex is IndexOutOfRangeException ||
                ex is InvalidOperationException ||
                ex is TypeLoadException ||
                ex is TypeInitializationException ||
                ex is InvalidCastException;
        }

        #endregion
    }
}
```

### WindowFlash class

This class makes a call to the **FlashWindow** method from the user32.dll to flash the WPF window when the conversation window needs attention.

```csharp
using System;
using System.Runtime.InteropServices;
using System.Windows;
using System.Windows.Forms;
using System.Windows.Interop;

namespace DockingConversationWindowSample
{
    /// <summary>
    /// This class helps in flashing a window to inform the user that the window 
    /// requires attention when it doesn't have the focus or is not active.
    /// </summary>
    class WindowFlash
    {
        #region Fields

        [DllImport("user32.dll")]
        private static extern bool FlashWindow(IntPtr hwnd, bool invert);

        private readonly Timer _clock;
        private readonly Boolean _flashing;
        private readonly Window _target;
        private const int Interval = 500;

        #endregion

        #region Constructor
        /// <summary>
        /// The constructor instantiates the window that requires flashing, the flashing, and the clock.
        /// </summary>
        public WindowFlash(Window sender, bool flashing)
        {
            _target = sender;
            _clock = new Timer();
            _flashing = flashing;
        }

        #endregion

        #region Public Methods

        /// <summary>
        /// This method starts the clock. The value of Inverval can be altered to change the speed of flashing.
        /// (default 500 mseconds)
        /// </summary>
        public void StartFlashing()
        {
            _clock.Interval = Interval;
            _clock.Start();
            _clock.Tick += ClockTick;
        }

        /// <summary>
        /// This method stops the clock
        /// </summary>
        public void StopFlashing()
        {
            _clock.Stop();
        }

        #endregion

        #region Private Methods

        /// <summary>
        /// This method gets fired when the clock ticks
        /// </summary>
        void ClockTick(object sender, EventArgs e)
        {
            IntPtr hwnd = new WindowInteropHelper(_target).Handle;
            FlashWindow(hwnd, !_flashing);
        }

        #endregion
    }
}
```

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

