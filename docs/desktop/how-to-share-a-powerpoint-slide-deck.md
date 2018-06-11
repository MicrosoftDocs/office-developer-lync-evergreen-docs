---
title: 'How to: Share a PowerPoint slide deck'
TOCTitle: 'How to: Share a PowerPoint slide deck'
ms:assetid: 5b7e68e7-9c7a-49b2-9541-19813682cef9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937325(v=office.15)
ms:contentKeyID: 50877159
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Share a PowerPoint slide deck

Learn how to use Microsoft Lync 2013 SDK to programmatically share a PowerPoint slide deck session in a Lync 2013 conversation.



**Applies to**: Lync 2013 | Lync Server 2013


<div class="caption">
Watch the video: Share PowerPoint slides in online meetings
</div>
<br />

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/07b2a385-8f2a-4745-abda-243d2a5dc26d]


## PowerPoint sharing overview

Learn how to create a shareable object that represents a PowerPoint deck, upload the shareable object to a conversation content bin, share it in a conversation, and then scroll through the slides.

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
<td><p>PowerPoint sharing is not supported in Lync UI suppression mode.</p></td>
</tr>
</tbody>
</table>

The sample application shown in figure 1 is a Windows Forms application that implements the Lync 2013 API to let a user manage PowerPoint sharing in a conversation.

Figure 1. Conversation whiteboard collaboration console

  
![PowerPoint presentation console slide navigation](images/JJ937325.UC_OCS15ConLyncClient_PowerPointNavfigure2(Office.15).png "PowerPoint presentation console slide navigation")

When a user uploads and selects the Project Plan slide deck from the console shown in figure 1, the slide deck is displayed in a Lync 2013 conversation window sharing stage as shown in figure 2.

Figure 2. PowerPoint deck shared in Lync 2013 conversation window

  
![Content stage with PowerPoint Deck shared](images/JJ937325.UC_OCS15ConLyncClient_PowerPointNavfigure1(Office.15).png "Content stage with PowerPoint Deck shared")

## Prerequisites

The prerequisites for sharing a PowerPoint deck are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

Understanding the following concepts is essential to using content sharing conversions in an application.

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
<td><p><a href="shareable-meeting-content.md">Shareable meeting content</a></p></td>
<td><p>Learn about the nature of shareable content in a Lync 2013 conversation and what content sharing feature that Microsoft Lync 2013 SDK lets you build into your application.</p></td>
</tr>
<tr class="even">
<td><p><a href="content-sharing-modality.md">Content sharing modality</a></p></td>
<td><p>Learn about the Lync 2013 conversation modality that is used to administer meeting content in an online meeting.</p></td>
</tr>
</tbody>
</table>

## First steps

Before the logic in this topic runs in your application, a conversation must be active and you have registered an event callback method for the **ContentSharingModalityActionAvailabilityChanged()** event. The [Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality](https://msdn.microsoft.com/en-us/library/jj266998\(v=office.15\)) is in a connected state. For information about starting a conversation that hosts content sharing, see [How to: Start a content sharing conversation](how-to-start-a-content-sharing-conversation.md).

### Code example: Namespace declarations

Add the following namespace declarations to your application.

```csharp
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;
using Microsoft.Lync.Model.Conversation;
using Microsoft.Lync.Model.Conversation.Sharing;
using System.Collections.Generic;
```

### Code example: Field declarations

Add the following class field declarations to your application.

``` 
        /// <summary>
        /// Lync client platform. The entry point to the API
        /// </summary>
        LyncClient _LyncClient;

        /// <summary>
        /// Represents a Lync conversation
        /// </summary>
        Conversation _conversation;
```

## Upload a PowerPoint deck to a conversation

When the [ModalityAction](https://msdn.microsoft.com/en-us/library/jj266957\(v=office.15\))**.CreateShareablePowerPointContent** action is available, you can create the [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/en-us/library/jj277217\(v=office.15\)) object that encapsulates the PowerPoint deck you upload.

### To upload a PowerPoint deck

1.  Verify that the **ShareableContent** object can be created by calling the [Modality.CanInvoke](https://msdn.microsoft.com/en-us/library/jj267958\(v=office.15\)) method.

2.  Create the **ShareableContent** object by calling the [ContentSharingModality.BeginCreateContentFromFile](https://msdn.microsoft.com/en-us/library/jj277389\(v=office.15\)) method.

3.  Upload the slide deck to the conversation by calling the [ShareableContent.Upload](https://msdn.microsoft.com/en-us/library/jj278338\(v=office.15\)) method on the **ShareableContent** object.

4.  Register for the [ShareableContent.ActionAvailabilityChanged](https://msdn.microsoft.com/en-us/library/jj267657\(v=office.15\)) event on the **ShareableContent** object.

### Code example: Create and upload a PowerPoint deck

The following example finishes first three steps of the previous procedure. The fourth step is completed in a following code example.

```csharp
        /// <summary>
        /// Raised when the availability of an action on the content sharing modality changes
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ActionAvailabilityChanged(object sender, ModalityActionAvailabilityChangedEventArgs e)
        {
            this.Invoke(new AddAListItemDelegate(AddAListItem), new object[] { EventLog_ListBox, "Content Modality, Action changed " + e.Action.ToString() + " " + e.IsAvailable.ToString() });

            EnableDisableButtonDelegate d = new EnableDisableButtonDelegate(EnableDisableButton);
            switch (e.Action)
            {
                case ModalityAction.CreateShareablePowerPointContent:

                    try
                    {
                        if (((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).CanInvoke(ModalityAction.CreateShareablePowerPointContent))
                        {
                            ContentSharingModality c = (ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing];
                            string contentTitle = "ProjectPlan.pptx";
                            c.BeginCreateContentFromFile(
                                ShareableContentType.PowerPoint,
                                contentTitle,
                                "//MyShare/ProjectPlan.pptx",
                                false,
                                CreateShareableContentCallback,
                                c);
                        }
                    }
                    catch (InvalidStateException ise) { MessageBox.Show("Invalid state exception on BeginCreateContent " + ise.Message); }
                    catch (NotInitializedException) { MessageBox.Show("Not initialized exception on BeginCreateContent "); }

                    break;
                case ModalityAction.Accept:
                    _RemoteParticipantSharingModality = (ContentSharingModality)sender;
                    this.Invoke(d, new object[] { Accept_Button, e.IsAvailable });
                    break;
                case ModalityAction.Reject:
                    this.Invoke(d, new object[] {Reject_Button, e.IsAvailable });
                    break;
            }
        }
```

The following example is invoked on the API platform thread when the **BeginCreateContentFromFile** operation is complete. The **\[T:Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality.EndCreateContentFromFile(System.IAsyncResult)\]** method is called and then the PowerPoint deck is uploaded with call to the [ShareableContent.Upload](https://msdn.microsoft.com/en-us/library/jj278338\(v=office.15\)) method.

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
<td><p>The three exceptions that are in the following catch blocks are raised for conditions that you cannot test for before you call the <strong>Upload</strong> method. This is because other conversation participants might be uploading content to the common conversation content bin at the same time that the local user is uploading the PowerPoint deck. Another participant might have selected the same content title as selected by the local user or uploaded the maximum number of content bin items.</p></td>
</tr>
</tbody>
</table>

```csharp
        /// <summary>
        /// Called by platform when ShareableContent object is created. 
        /// Uploads the PowerPoint slide deck to the conversation content bin
        /// where it is available to be shared (Presented)
        /// </summary>
        /// <param name="ar"></param>
        private void CreateShareableContentCallback(System.IAsyncResult ar)
        {
            try
            {
                ContentSharingModality shareModality = (ContentSharingModality)ar.AsyncState;
                ShareableContent sContent = shareModality.EndCreateContentFromFile(ar);
                sContent.Upload();
            }
            catch (MaxContentsExceededException) {
                MessageBox.Show("Content was not uploaded. You have reached the maximum number of content bin items");
            }
            catch (ContentTitleExistException) {
                MessageBox.Show("Content was not uploaded. Content title already exists");
            }
            catch (ContentTitleInvalidException) {
                MessageBox.Show("Content was not uploaded. Content title is not valid");
            }
        }
```

### Code example: Register for the ShareableContent.ActionAvailabilityChanged event

The following example registers event callback methods on the new **SharingModality** object events.

``` 
        /// <summary>
        /// Raised when an item is uploaded to the content bin
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ContentAdded(object sender, ContentCollectionChangedEventArgs e)
        {
            e.Item.StateChanged += _ShareableContent_StateChanged;
            e.Item.ActionAvailabilityChanged += _ShareableContent_ActionAvailabilityChanged;
        }
```

### Code example: Handle the ActionAvailabilityChanged event

The following example enables or disables the content item sharing UI command buttons when the availability of actions on the [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/en-us/library/jj277217\(v=office.15\)) object changes.

```csharp
        /// <summary>
        /// Raised when the availability of an action on a ShareableContent object changes
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _ShareableContent_ActionAvailabilityChanged(object sender, ShareableContentActionAvailabilityChangedEventArgs e)
        {
            EnableDisableButtonDelegate d = new EnableDisableButtonDelegate(EnableDisableButton);
            switch (e.Action)
            {
                case ShareableContentAction.SaveAnnotation:
                    this.Invoke(d, new object[] { SaveAnnotations_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.ClearAllAnnotations:
                    this.Invoke(d, new object[] { ClearAnnotations_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.SyncWithPresenter:
                    this.Invoke(d, new object[] { SyncWithPresenter_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.TakeOverAsPresenter:
                    this.Invoke(d, new object[] { TakeOverAsPresenter_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.StopPresenting:
                    this.Invoke(d, new object[] { StopSharingContent_Button, e.IsAvailable });
                    break;
            }
        }

        private delegate void EnableDisableButtonDelegate(Button buttonToUpdate, Boolean newButtonEnableState);
        /// <summary>
        /// Enables or disables a UI button based on the actionAvailability
        /// </summary>
        /// <param name="buttonToUpdate"></param>
        /// <param name="newButtonEnableState"></param>
        private void EnableDisableButton(Button buttonToUpdate, Boolean newButtonEnableState)
        {
            buttonToUpdate.Enabled = newButtonEnableState;
        }
```

## Share a PowerPoint deck

To share a whiteboard, call the [ShareableContent.Present](https://msdn.microsoft.com/en-us/library/jj276346\(v=office.15\)) method on the content object that you want to share. If other content is being presented, it is displaced on the content sharing stage by the content sharing object on which you called the **Present** method.

### To share a PowerPoint deck

1.  Iterate on the [ContentSharingModality.ContentCollection](https://msdn.microsoft.com/en-us/library/jj267301\(v=office.15\)) property to find the [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/en-us/library/jj277217\(v=office.15\)) object whose [ShareableContent.Title](https://msdn.microsoft.com/en-us/library/jj293276\(v=office.15\)) property matches the title that you want to share.

2.  Verify that the content can be presented by calling the [ShareableContent.CanInvoke](https://msdn.microsoft.com/en-us/library/jj275741\(v=office.15\)) method.

3.  Share the content by calling the [ShareableContent.Present](https://msdn.microsoft.com/en-us/library/jj276346\(v=office.15\)) method.

### Code example: Content item

The following example presents the content item whose title is "Project Plan."

```csharp
            //Iterate on content collection of conversation content sharing modality,
            //looking for the content whose title matches the string selected in the
            //list.
            foreach (ShareableContent sContent in ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).ContentCollection)
            {
                if (sContent.Title == "Project Plan")
                {
                    int hrReason;
                    if (sContent.CanInvoke(ShareableContentAction.Present, out hrReason))
                    {
                        _ShareableContent = sContent;
                        sContent.Present();
                    }
                    else
                    {
                        MessageBox.Show("Cannot present whiteboard: " + hrReason.ToString());
                    }
                    break;
                }
            }
```

## Scroll through PowerPoint slides in a conversation

Scrolling through an active PowerPoint presentation in a conversation involves making one of three synchronous method calls. To go back one slide in the deck, call the [PowerPointContent.GoBackward](https://msdn.microsoft.com/en-us/library/jj293484\(v=office.15\)) method. To go forward one slide, call the [PowerPointContent.GoForward](https://msdn.microsoft.com/en-us/library/jj277967\(v=office.15\)) method. To return the view to meeting view mode, call the [PowerPointContent.SyncWithPresenter](https://msdn.microsoft.com/en-us/library/jj277002\(v=office.15\)) method. These two methods are exposed on a subclass of [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/en-us/library/jj277217\(v=office.15\)) so that you need to cast the **ShareableContent** object that encapsulates the active PowerPoint presentation into the [Microsoft.Lync.Model.Conversation.Sharing.PowerPointContent](https://msdn.microsoft.com/en-us/library/jj277028\(v=office.15\)) class before you can scroll through the slides.

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
<td><p>When the local user is a presenter in the conversation, scrolling behaves differently than when the user is an attendee. When a presenter is sharing a PowerPoint slide deck and scrolls the deck in either direction, it is scrolled for all conversation participants. If the local user is an attendee instead of a presenter, scrolling changes only the local view of the slide deck. When an attendee scrolls, the PowerPoint presentation is put into private viewing mode.</p></td>
</tr>
</tbody>
</table>

### To scroll through PowerPoint slides

1.  Get the active content sharing object on the sharing stage of the conversation.

2.  Verify that the object is of type [ShareableContentType](https://msdn.microsoft.com/en-us/library/jj275743\(v=office.15\))**.PowerPoint**.

3.  Cast the shareable content object to the [Microsoft.Lync.Model.Conversation.Sharing.PowerPointContent](https://msdn.microsoft.com/en-us/library/jj277028\(v=office.15\)) class.

4.  Call the [PowerPointContent.GoForward](https://msdn.microsoft.com/en-us/library/jj277967\(v=office.15\)), [PowerPointContent.GoBackward](https://msdn.microsoft.com/en-us/library/jj293484\(v=office.15\)), or [PowerPointContent.SyncWithPresenter](https://msdn.microsoft.com/en-us/library/jj277002\(v=office.15\)) method.

### Code example: Scroll backward and forward

The following examples scroll backward and forward one slide in the active PowerPoint slide deck.

```csharp
        /// <summary>
        /// Scroll back one slide in the active PowerPoint slide deck.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void GoBack_Button_Click(object sender, EventArgs e)
        {
            ShareableContent currentActiveContent = ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).ActiveContent;
            if (currentActiveContent.Type == ShareableContentType.PowerPoint)
            {
                PowerPointContent ppc = currentActiveContent as PowerPointContent;
                ppc.GoBackward();
            }
        }

        /// <summary>
        /// Scroll forward one slide in the active PowerPoint slide deck.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void GoForward_Button_Click(object sender, EventArgs e)
        {
            ShareableContent currentActiveContent = ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).ActiveContent;
            if (currentActiveContent.Type == ShareableContentType.PowerPoint)
            {
                PowerPointContent ppc = currentActiveContent as PowerPointContent;
                ppc.GoForward();
            }

        }
```

## Application state after you complete all tasks

When all these tasks are completed, the state of Lync 2013 API objects are as described in the following table.

Lync 2013 API conversation objects

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Object</p></th>
<th><p>Description</p></th>
<th><p>State</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj274980(v=office.15)">Microsoft.Lync.Model.LyncClient</a></p></td>
<td><p>The client platform API entry point.</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275269(v=office.15)">ClientState</a><strong>.SignedIn</strong></p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276988(v=office.15)">Microsoft.Lync.Model.Conversation.Conversation</a></p></td>
<td><p>The content sharing conversation.</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277587(v=office.15)">Microsoft.Lync.Model.Conversation.ConversationState</a><strong>.Active</strong></p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266998(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality</a></p></td>
<td><p>The conversation content sharing modality.</p>
<div class="alert">
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Note" alt="Note" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Each participant in the active conversation exposes a collection of modalities that include a content sharing modality. Each of these content sharing modality objects is also connected.</p></td>
</tr>
</tbody>
</table>
</div></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293265(v=office.15)">ModalityState</a><strong>.Connected</strong></p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277217(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ShareableContent</a></p></td>
<td><p>The PowerPoint deck that is uploaded and shared in the conversation.</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267322(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState</a><strong>.Active</strong></p>
<div class="alert">
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Note" alt="Note" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>If you are no longer sharing the PowerPoint deck, the status is <a href="https://msdn.microsoft.com/en-us/library/jj267322(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState</a><strong>.Online</strong>.</p></td>
</tr>
</tbody>
</table>
</div></td>
</tr>
</tbody>
</table>

## Code examples: Quick meeting console

The following example declares the Windows Form shown in figure 1.

```csharp
namespace ContentSharing
{
    partial class ContentSharing_Form
    {
        /// <summary>
        /// Required designer variable.
        /// </summary>
        private System.ComponentModel.IContainer components = null;

        /// <summary>
        /// Clean up any resources being used.
        /// </summary>
        /// <param name="disposing">true if managed resources should be disposed; otherwise, false.</param>
        protected override void Dispose(bool disposing)
        {
            if (disposing && (components != null))
            {
                components.Dispose();
            }
            base.Dispose(disposing);
        }

        #region Windows Form Designer generated code

        /// <summary>
        /// Required method for Designer support - do not modify
        /// the contents of this method with the code editor.
        /// </summary>
        private void InitializeComponent()
        {
            this.ClientState_Label = new System.Windows.Forms.Label();
            this.ClientStateString_Label = new System.Windows.Forms.Label();
            this.Contact_ListBox = new System.Windows.Forms.ListBox();
            this.ConversationActions_Group = new System.Windows.Forms.GroupBox();
            this.EndConversation_Button = new System.Windows.Forms.Button();
            this.Start_Button = new System.Windows.Forms.Button();
            this.ContactList_Label = new System.Windows.Forms.Label();
            this.Content_Listbox = new System.Windows.Forms.ListBox();
            this.label1 = new System.Windows.Forms.Label();
            this.ShareableContentTitle_Textbox = new System.Windows.Forms.TextBox();
            this.ShareWhiteboard_Button = new System.Windows.Forms.Button();
            this.ContentShare_Button = new System.Windows.Forms.Button();
            this.StopSharingContent_Button = new System.Windows.Forms.Button();
            this.PickContentItemPath_OpenFileDialog = new System.Windows.Forms.OpenFileDialog();
            this.PickAPowerPoint_Button = new System.Windows.Forms.Button();
            this.PickNativeFile_Button = new System.Windows.Forms.Button();
            this.DownloadAttachment_Button = new System.Windows.Forms.Button();
            this.Accept_Button = new System.Windows.Forms.Button();
            this.Reject_Button = new System.Windows.Forms.Button();
            this.ModalityConnectedState_Panel = new System.Windows.Forms.Panel();
            this.ActiveContent_Label = new System.Windows.Forms.Label();
            this.ClearAnnotations_Button = new System.Windows.Forms.Button();
            this.SaveAnnotations_Button = new System.Windows.Forms.Button();
            this.SyncWithPresenter_Button = new System.Windows.Forms.Button();
            this.TakeOverAsPresenter_Button = new System.Windows.Forms.Button();
            this.GoBack_Button = new System.Windows.Forms.Button();
            this.GoForward_Button = new System.Windows.Forms.Button();
            this.StartConversation_Group = new System.Windows.Forms.GroupBox();
            this.ModalityState_Label = new System.Windows.Forms.Label();
            this.ContentBin_Groupbox = new System.Windows.Forms.GroupBox();
            this.groupBox3 = new System.Windows.Forms.GroupBox();
            this.groupBox2 = new System.Windows.Forms.GroupBox();
            this.AddNativeFile_Button = new System.Windows.Forms.Button();
            this.groupBox1 = new System.Windows.Forms.GroupBox();
            this.AddPowerPoint_Button = new System.Windows.Forms.Button();
            this.ContentItem_GroupBox = new System.Windows.Forms.GroupBox();
            this.label2 = new System.Windows.Forms.Label();
            this.RefreshContent_Button = new System.Windows.Forms.Button();
            this.RemoveFromBin_Button = new System.Windows.Forms.Button();
            this.SharingInvitation_Groupbox = new System.Windows.Forms.GroupBox();
            this.DownloadFolderBrowser_FolderBrowser = new System.Windows.Forms.FolderBrowserDialog();
            this.SetBusy_Button = new System.Windows.Forms.Button();
            this.Alerts_Button = new System.Windows.Forms.Button();
            this.ConversationActions_Group.SuspendLayout();
            this.StartConversation_Group.SuspendLayout();
            this.ContentBin_Groupbox.SuspendLayout();
            this.groupBox3.SuspendLayout();
            this.groupBox2.SuspendLayout();
            this.groupBox1.SuspendLayout();
            this.ContentItem_GroupBox.SuspendLayout();
            this.SharingInvitation_Groupbox.SuspendLayout();
            this.SuspendLayout();
            // 
            // ClientState_Label
            // 
            this.ClientState_Label.AutoSize = true;
            this.ClientState_Label.Location = new System.Drawing.Point(16, 7);
            this.ClientState_Label.Name = "ClientState_Label";
            this.ClientState_Label.Size = new System.Drawing.Size(64, 13);
            this.ClientState_Label.TabIndex = 0;
            this.ClientState_Label.Text = "Client State:";
            // 
            // ClientStateString_Label
            // 
            this.ClientStateString_Label.AutoSize = true;
            this.ClientStateString_Label.Location = new System.Drawing.Point(115, 9);
            this.ClientStateString_Label.Name = "ClientStateString_Label";
            this.ClientStateString_Label.Size = new System.Drawing.Size(58, 13);
            this.ClientStateString_Label.TabIndex = 1;
            this.ClientStateString_Label.Text = "Signed out";
            // 
            // Contact_ListBox
            // 
            this.Contact_ListBox.FormattingEnabled = true;
            this.Contact_ListBox.HorizontalScrollbar = true;
            this.Contact_ListBox.Location = new System.Drawing.Point(6, 37);
            this.Contact_ListBox.Name = "Contact_ListBox";
            this.Contact_ListBox.SelectionMode = System.Windows.Forms.SelectionMode.MultiSimple;
            this.Contact_ListBox.Size = new System.Drawing.Size(204, 69);
            this.Contact_ListBox.TabIndex = 2;
            // 
            // ConversationActions_Group
            // 
            this.ConversationActions_Group.Controls.Add(this.EndConversation_Button);
            this.ConversationActions_Group.Controls.Add(this.Start_Button);
            this.ConversationActions_Group.Location = new System.Drawing.Point(6, 119);
            this.ConversationActions_Group.Name = "ConversationActions_Group";
            this.ConversationActions_Group.Size = new System.Drawing.Size(204, 83);
            this.ConversationActions_Group.TabIndex = 13;
            this.ConversationActions_Group.TabStop = false;
            this.ConversationActions_Group.Text = "Start a conversation";
            // 
            // EndConversation_Button
            // 
            this.EndConversation_Button.Enabled = false;
            this.EndConversation_Button.Location = new System.Drawing.Point(16, 52);
            this.EndConversation_Button.Name = "EndConversation_Button";
            this.EndConversation_Button.Size = new System.Drawing.Size(163, 23);
            this.EndConversation_Button.TabIndex = 0;
            this.EndConversation_Button.Text = "End";
            this.EndConversation_Button.UseVisualStyleBackColor = true;
            this.EndConversation_Button.Click += new System.EventHandler(this.EndConversation_Button_Click);
            // 
            // Start_Button
            // 
            this.Start_Button.Enabled = false;
            this.Start_Button.Location = new System.Drawing.Point(16, 23);
            this.Start_Button.Name = "Start_Button";
            this.Start_Button.Size = new System.Drawing.Size(163, 23);
            this.Start_Button.TabIndex = 16;
            this.Start_Button.Text = "Start";
            this.Start_Button.UseVisualStyleBackColor = true;
            this.Start_Button.Click += new System.EventHandler(this.Start_Button_Click);
            // 
            // ContactList_Label
            // 
            this.ContactList_Label.AutoSize = true;
            this.ContactList_Label.Location = new System.Drawing.Point(6, 21);
            this.ContactList_Label.Name = "ContactList_Label";
            this.ContactList_Label.Size = new System.Drawing.Size(92, 13);
            this.ContactList_Label.TabIndex = 20;
            this.ContactList_Label.Text = "People in Meeting";
            // 
            // Content_Listbox
            // 
            this.Content_Listbox.FormattingEnabled = true;
            this.Content_Listbox.Location = new System.Drawing.Point(24, 97);
            this.Content_Listbox.Name = "Content_Listbox";
            this.Content_Listbox.Size = new System.Drawing.Size(175, 82);
            this.Content_Listbox.TabIndex = 21;
            this.Content_Listbox.SelectedIndexChanged += new System.EventHandler(this.Content_Listbox_SelectedIndexChanged);
            // 
            // label1
            // 
            this.label1.AutoSize = true;
            this.label1.Location = new System.Drawing.Point(10, 16);
            this.label1.Name = "label1";
            this.label1.Size = new System.Drawing.Size(113, 13);
            this.label1.TabIndex = 29;
            this.label1.Text = "New Whiteboard Title:";
            // 
            // ShareableContentTitle_Textbox
            // 
            this.ShareableContentTitle_Textbox.Location = new System.Drawing.Point(20, 32);
            this.ShareableContentTitle_Textbox.Name = "ShareableContentTitle_Textbox";
            this.ShareableContentTitle_Textbox.Size = new System.Drawing.Size(96, 20);
            this.ShareableContentTitle_Textbox.TabIndex = 30;
            // 
            // ShareWhiteboard_Button
            // 
            this.ShareWhiteboard_Button.Location = new System.Drawing.Point(17, 58);
            this.ShareWhiteboard_Button.Name = "ShareWhiteboard_Button";
            this.ShareWhiteboard_Button.Size = new System.Drawing.Size(163, 23);
            this.ShareWhiteboard_Button.TabIndex = 32;
            this.ShareWhiteboard_Button.Text = "Add Whiteboard";
            this.ShareWhiteboard_Button.UseVisualStyleBackColor = true;
            this.ShareWhiteboard_Button.Click += new System.EventHandler(this.ShareNewContent_Button_Click);
            // 
            // ContentShare_Button
            // 
            this.ContentShare_Button.Enabled = false;
            this.ContentShare_Button.Location = new System.Drawing.Point(25, 257);
            this.ContentShare_Button.Name = "ContentShare_Button";
            this.ContentShare_Button.Size = new System.Drawing.Size(174, 23);
            this.ContentShare_Button.TabIndex = 34;
            this.ContentShare_Button.Text = "Share Content";
            this.ContentShare_Button.UseVisualStyleBackColor = true;
            this.ContentShare_Button.Click += new System.EventHandler(this.ContentShare_Button_Click);
            // 
            // StopSharingContent_Button
            // 
            this.StopSharingContent_Button.Enabled = false;
            this.StopSharingContent_Button.Location = new System.Drawing.Point(25, 282);
            this.StopSharingContent_Button.Name = "StopSharingContent_Button";
            this.StopSharingContent_Button.Size = new System.Drawing.Size(174, 23);
            this.StopSharingContent_Button.TabIndex = 35;
            this.StopSharingContent_Button.Text = "Stop Sharing";
            this.StopSharingContent_Button.UseVisualStyleBackColor = true;
            this.StopSharingContent_Button.Click += new System.EventHandler(this.StopSharingContent_Button_Click);
            // 
            // PickContentItemPath_OpenFileDialog
            // 
            this.PickContentItemPath_OpenFileDialog.FileName = "ABriefHistoryofThyme.pptx";
            this.PickContentItemPath_OpenFileDialog.InitialDirectory = "Libraries\\Documents";
            // 
            // PickAPowerPoint_Button
            // 
            this.PickAPowerPoint_Button.Location = new System.Drawing.Point(13, 19);
            this.PickAPowerPoint_Button.Name = "PickAPowerPoint_Button";
            this.PickAPowerPoint_Button.Size = new System.Drawing.Size(163, 23);
            this.PickAPowerPoint_Button.TabIndex = 36;
            this.PickAPowerPoint_Button.Text = "Pick PowerPoint Deck";
            this.PickAPowerPoint_Button.UseVisualStyleBackColor = true;
            this.PickAPowerPoint_Button.Click += new System.EventHandler(this.PickAPowerPoint_Button_Click);
            // 
            // PickNativeFile_Button
            // 
            this.PickNativeFile_Button.Location = new System.Drawing.Point(12, 19);
            this.PickNativeFile_Button.Name = "PickNativeFile_Button";
            this.PickNativeFile_Button.Size = new System.Drawing.Size(163, 23);
            this.PickNativeFile_Button.TabIndex = 37;
            this.PickNativeFile_Button.Text = "Pick Attachment";
            this.PickNativeFile_Button.UseVisualStyleBackColor = true;
            this.PickNativeFile_Button.Click += new System.EventHandler(this.PickNativeFile_Button_Click);
            // 
            // DownloadAttachment_Button
            // 
            this.DownloadAttachment_Button.Enabled = false;
            this.DownloadAttachment_Button.Location = new System.Drawing.Point(25, 382);
            this.DownloadAttachment_Button.Name = "DownloadAttachment_Button";
            this.DownloadAttachment_Button.Size = new System.Drawing.Size(175, 23);
            this.DownloadAttachment_Button.TabIndex = 38;
            this.DownloadAttachment_Button.Text = "Download Attachment";
            this.DownloadAttachment_Button.UseVisualStyleBackColor = true;
            this.DownloadAttachment_Button.Click += new System.EventHandler(this.DownloadAttachment_Button_Click);
            // 
            // Accept_Button
            // 
            this.Accept_Button.Enabled = false;
            this.Accept_Button.Location = new System.Drawing.Point(8, 27);
            this.Accept_Button.Name = "Accept_Button";
            this.Accept_Button.Size = new System.Drawing.Size(99, 23);
            this.Accept_Button.TabIndex = 39;
            this.Accept_Button.Text = "Acccept";
            this.Accept_Button.UseVisualStyleBackColor = true;
            this.Accept_Button.Click += new System.EventHandler(this.Accept_Button_Click);
            // 
            // Reject_Button
            // 
            this.Reject_Button.Enabled = false;
            this.Reject_Button.Location = new System.Drawing.Point(122, 27);
            this.Reject_Button.Name = "Reject_Button";
            this.Reject_Button.Size = new System.Drawing.Size(99, 23);
            this.Reject_Button.TabIndex = 40;
            this.Reject_Button.Text = "Reject";
            this.Reject_Button.UseVisualStyleBackColor = true;
            this.Reject_Button.Click += new System.EventHandler(this.Reject_Button_Click);
            // 
            // ModalityConnectedState_Panel
            // 
            this.ModalityConnectedState_Panel.BackColor = System.Drawing.Color.Red;
            this.ModalityConnectedState_Panel.Location = new System.Drawing.Point(178, 377);
            this.ModalityConnectedState_Panel.Name = "ModalityConnectedState_Panel";
            this.ModalityConnectedState_Panel.Size = new System.Drawing.Size(35, 13);
            this.ModalityConnectedState_Panel.TabIndex = 41;
            // 
            // ActiveContent_Label
            // 
            this.ActiveContent_Label.AutoSize = true;
            this.ActiveContent_Label.Location = new System.Drawing.Point(18, 33);
            this.ActiveContent_Label.Name = "ActiveContent_Label";
            this.ActiveContent_Label.Size = new System.Drawing.Size(80, 13);
            this.ActiveContent_Label.TabIndex = 43;
            this.ActiveContent_Label.Text = "Active Content:";
            // 
            // ClearAnnotations_Button
            // 
            this.ClearAnnotations_Button.Enabled = false;
            this.ClearAnnotations_Button.Location = new System.Drawing.Point(25, 307);
            this.ClearAnnotations_Button.Name = "ClearAnnotations_Button";
            this.ClearAnnotations_Button.Size = new System.Drawing.Size(175, 23);
            this.ClearAnnotations_Button.TabIndex = 44;
            this.ClearAnnotations_Button.Text = "Clear Annotations";
            this.ClearAnnotations_Button.UseVisualStyleBackColor = true;
            this.ClearAnnotations_Button.Click += new System.EventHandler(this.ClearAnnotations_Button_Click);
            // 
            // SaveAnnotations_Button
            // 
            this.SaveAnnotations_Button.Enabled = false;
            this.SaveAnnotations_Button.Location = new System.Drawing.Point(25, 332);
            this.SaveAnnotations_Button.Name = "SaveAnnotations_Button";
            this.SaveAnnotations_Button.Size = new System.Drawing.Size(174, 23);
            this.SaveAnnotations_Button.TabIndex = 45;
            this.SaveAnnotations_Button.Text = "Save Annotations";
            this.SaveAnnotations_Button.UseVisualStyleBackColor = true;
            this.SaveAnnotations_Button.Click += new System.EventHandler(this.SaveAnnotations_Button_Click);
            // 
            // SyncWithPresenter_Button
            // 
            this.SyncWithPresenter_Button.Enabled = false;
            this.SyncWithPresenter_Button.Location = new System.Drawing.Point(25, 407);
            this.SyncWithPresenter_Button.Name = "SyncWithPresenter_Button";
            this.SyncWithPresenter_Button.Size = new System.Drawing.Size(174, 23);
            this.SyncWithPresenter_Button.TabIndex = 46;
            this.SyncWithPresenter_Button.Text = "Return to meeting view";
            this.SyncWithPresenter_Button.UseVisualStyleBackColor = true;
            this.SyncWithPresenter_Button.Click += new System.EventHandler(this.SyncWithPresenter_Button_Click);
            // 
            // TakeOverAsPresenter_Button
            // 
            this.TakeOverAsPresenter_Button.Enabled = false;
            this.TakeOverAsPresenter_Button.Location = new System.Drawing.Point(25, 357);
            this.TakeOverAsPresenter_Button.Name = "TakeOverAsPresenter_Button";
            this.TakeOverAsPresenter_Button.Size = new System.Drawing.Size(175, 23);
            this.TakeOverAsPresenter_Button.TabIndex = 47;
            this.TakeOverAsPresenter_Button.Text = "Take Over as Presenter";
            this.TakeOverAsPresenter_Button.UseVisualStyleBackColor = true;
            this.TakeOverAsPresenter_Button.Click += new System.EventHandler(this.TakeOverAsPresenter_Button_Click);
            // 
            // GoBack_Button
            // 
            this.GoBack_Button.Enabled = false;
            this.GoBack_Button.Location = new System.Drawing.Point(24, 439);
            this.GoBack_Button.Name = "GoBack_Button";
            this.GoBack_Button.Size = new System.Drawing.Size(75, 23);
            this.GoBack_Button.TabIndex = 48;
            this.GoBack_Button.Text = "<<";
            this.GoBack_Button.UseVisualStyleBackColor = true;
            this.GoBack_Button.Click += new System.EventHandler(this.GoBack_Button_Click_1);
            // 
            // GoForward_Button
            // 
            this.GoForward_Button.Enabled = false;
            this.GoForward_Button.Location = new System.Drawing.Point(124, 439);
            this.GoForward_Button.Name = "GoForward_Button";
            this.GoForward_Button.Size = new System.Drawing.Size(75, 23);
            this.GoForward_Button.TabIndex = 49;
            this.GoForward_Button.Text = ">>";
            this.GoForward_Button.UseVisualStyleBackColor = true;
            this.GoForward_Button.Click += new System.EventHandler(this.GoForward_Button_Click_1);
            // 
            // StartConversation_Group
            // 
            this.StartConversation_Group.Controls.Add(this.Contact_ListBox);
            this.StartConversation_Group.Controls.Add(this.ConversationActions_Group);
            this.StartConversation_Group.Controls.Add(this.ContactList_Label);
            this.StartConversation_Group.Location = new System.Drawing.Point(12, 48);
            this.StartConversation_Group.Name = "StartConversation_Group";
            this.StartConversation_Group.Size = new System.Drawing.Size(226, 215);
            this.StartConversation_Group.TabIndex = 50;
            this.StartConversation_Group.TabStop = false;
            this.StartConversation_Group.Text = "Conversation";
            // 
            // ModalityState_Label
            // 
            this.ModalityState_Label.AutoSize = true;
            this.ModalityState_Label.Location = new System.Drawing.Point(7, 377);
            this.ModalityState_Label.Name = "ModalityState_Label";
            this.ModalityState_Label.Size = new System.Drawing.Size(165, 13);
            this.ModalityState_Label.TabIndex = 42;
            this.ModalityState_Label.Text = "State of Content Sharing Modality";
            // 
            // ContentBin_Groupbox
            // 
            this.ContentBin_Groupbox.Controls.Add(this.ModalityState_Label);
            this.ContentBin_Groupbox.Controls.Add(this.ModalityConnectedState_Panel);
            this.ContentBin_Groupbox.Controls.Add(this.groupBox3);
            this.ContentBin_Groupbox.Controls.Add(this.groupBox2);
            this.ContentBin_Groupbox.Controls.Add(this.groupBox1);
            this.ContentBin_Groupbox.Location = new System.Drawing.Point(12, 286);
            this.ContentBin_Groupbox.Name = "ContentBin_Groupbox";
            this.ContentBin_Groupbox.Size = new System.Drawing.Size(226, 424);
            this.ContentBin_Groupbox.TabIndex = 52;
            this.ContentBin_Groupbox.TabStop = false;
            this.ContentBin_Groupbox.Text = "Content Bin Management";
            // 
            // groupBox3
            // 
            this.groupBox3.Controls.Add(this.ShareableContentTitle_Textbox);
            this.groupBox3.Controls.Add(this.label1);
            this.groupBox3.Controls.Add(this.ShareWhiteboard_Button);
            this.groupBox3.Location = new System.Drawing.Point(10, 33);
            this.groupBox3.Name = "groupBox3";
            this.groupBox3.Size = new System.Drawing.Size(200, 100);
            this.groupBox3.TabIndex = 44;
            this.groupBox3.TabStop = false;
            this.groupBox3.Text = "Whiteboard";
            // 
            // groupBox2
            // 
            this.groupBox2.Controls.Add(this.PickNativeFile_Button);
            this.groupBox2.Controls.Add(this.AddNativeFile_Button);
            this.groupBox2.Location = new System.Drawing.Point(9, 256);
            this.groupBox2.Name = "groupBox2";
            this.groupBox2.Size = new System.Drawing.Size(200, 86);
            this.groupBox2.TabIndex = 43;
            this.groupBox2.TabStop = false;
            this.groupBox2.Text = "Attachment";
            // 
            // AddNativeFile_Button
            // 
            this.AddNativeFile_Button.Location = new System.Drawing.Point(12, 48);
            this.AddNativeFile_Button.Name = "AddNativeFile_Button";
            this.AddNativeFile_Button.Size = new System.Drawing.Size(163, 23);
            this.AddNativeFile_Button.TabIndex = 39;
            this.AddNativeFile_Button.Text = "Upload Attachment";
            this.AddNativeFile_Button.UseVisualStyleBackColor = true;
            this.AddNativeFile_Button.Click += new System.EventHandler(this.UploadNativeFile_Button_Click);
            // 
            // groupBox1
            // 
            this.groupBox1.Controls.Add(this.PickAPowerPoint_Button);
            this.groupBox1.Controls.Add(this.AddPowerPoint_Button);
            this.groupBox1.Location = new System.Drawing.Point(9, 156);
            this.groupBox1.Name = "groupBox1";
            this.groupBox1.Size = new System.Drawing.Size(201, 86);
            this.groupBox1.TabIndex = 42;
            this.groupBox1.TabStop = false;
            this.groupBox1.Text = "PowerPoint";
            // 
            // AddPowerPoint_Button
            // 
            this.AddPowerPoint_Button.Location = new System.Drawing.Point(13, 46);
            this.AddPowerPoint_Button.Name = "AddPowerPoint_Button";
            this.AddPowerPoint_Button.Size = new System.Drawing.Size(163, 23);
            this.AddPowerPoint_Button.TabIndex = 38;
            this.AddPowerPoint_Button.Text = "Upload PowerPoint";
            this.AddPowerPoint_Button.UseVisualStyleBackColor = true;
            this.AddPowerPoint_Button.Click += new System.EventHandler(this.AddPowerPoint_Button_Click);
            // 
            // ContentItem_GroupBox
            // 
            this.ContentItem_GroupBox.Controls.Add(this.label2);
            this.ContentItem_GroupBox.Controls.Add(this.RefreshContent_Button);
            this.ContentItem_GroupBox.Controls.Add(this.RemoveFromBin_Button);
            this.ContentItem_GroupBox.Controls.Add(this.Content_Listbox);
            this.ContentItem_GroupBox.Controls.Add(this.ContentShare_Button);
            this.ContentItem_GroupBox.Controls.Add(this.StopSharingContent_Button);
            this.ContentItem_GroupBox.Controls.Add(this.GoForward_Button);
            this.ContentItem_GroupBox.Controls.Add(this.DownloadAttachment_Button);
            this.ContentItem_GroupBox.Controls.Add(this.GoBack_Button);
            this.ContentItem_GroupBox.Controls.Add(this.ActiveContent_Label);
            this.ContentItem_GroupBox.Controls.Add(this.TakeOverAsPresenter_Button);
            this.ContentItem_GroupBox.Controls.Add(this.ClearAnnotations_Button);
            this.ContentItem_GroupBox.Controls.Add(this.SyncWithPresenter_Button);
            this.ContentItem_GroupBox.Controls.Add(this.SaveAnnotations_Button);
            this.ContentItem_GroupBox.Location = new System.Drawing.Point(252, 149);
            this.ContentItem_GroupBox.Name = "ContentItem_GroupBox";
            this.ContentItem_GroupBox.Size = new System.Drawing.Size(219, 561);
            this.ContentItem_GroupBox.TabIndex = 53;
            this.ContentItem_GroupBox.TabStop = false;
            this.ContentItem_GroupBox.Text = "Shared Content Actions";
            // 
            // label2
            // 
            this.label2.AutoSize = true;
            this.label2.Location = new System.Drawing.Point(21, 79);
            this.label2.Name = "label2";
            this.label2.Size = new System.Drawing.Size(103, 13);
            this.label2.TabIndex = 56;
            this.label2.Text = "Meeting Content Bin";
            // 
            // RefreshContent_Button
            // 
            this.RefreshContent_Button.Location = new System.Drawing.Point(24, 226);
            this.RefreshContent_Button.Name = "RefreshContent_Button";
            this.RefreshContent_Button.Size = new System.Drawing.Size(175, 25);
            this.RefreshContent_Button.TabIndex = 55;
            this.RefreshContent_Button.Text = "Refresh Content List";
            this.RefreshContent_Button.UseVisualStyleBackColor = true;
            this.RefreshContent_Button.Click += new System.EventHandler(this.RefreshContent_Button_Click);
            // 
            // RemoveFromBin_Button
            // 
            this.RemoveFromBin_Button.Location = new System.Drawing.Point(24, 197);
            this.RemoveFromBin_Button.Name = "RemoveFromBin_Button";
            this.RemoveFromBin_Button.Size = new System.Drawing.Size(175, 23);
            this.RemoveFromBin_Button.TabIndex = 50;
            this.RemoveFromBin_Button.Text = "Remove";
            this.RemoveFromBin_Button.UseVisualStyleBackColor = true;
            this.RemoveFromBin_Button.Click += new System.EventHandler(this.RemoveFromBin_Button_Click);
            // 
            // SharingInvitation_Groupbox
            // 
            this.SharingInvitation_Groupbox.Controls.Add(this.Reject_Button);
            this.SharingInvitation_Groupbox.Controls.Add(this.Accept_Button);
            this.SharingInvitation_Groupbox.Location = new System.Drawing.Point(244, 48);
            this.SharingInvitation_Groupbox.Name = "SharingInvitation_Groupbox";
            this.SharingInvitation_Groupbox.Size = new System.Drawing.Size(227, 60);
            this.SharingInvitation_Groupbox.TabIndex = 54;
            this.SharingInvitation_Groupbox.TabStop = false;
            this.SharingInvitation_Groupbox.Text = "Content Sharing Invitation";
            // 
            // DownloadFolderBrowser_FolderBrowser
            // 
            this.DownloadFolderBrowser_FolderBrowser.RootFolder = System.Environment.SpecialFolder.CommonDocuments;
            this.DownloadFolderBrowser_FolderBrowser.SelectedPath = "C:\\Users\\Public";
            // 
            // SetBusy_Button
            // 
            this.SetBusy_Button.Location = new System.Drawing.Point(244, 9);
            this.SetBusy_Button.Name = "SetBusy_Button";
            this.SetBusy_Button.Size = new System.Drawing.Size(142, 23);
            this.SetBusy_Button.TabIndex = 55;
            this.SetBusy_Button.Text = "Set In Meeting status";
            this.SetBusy_Button.UseVisualStyleBackColor = true;
            this.SetBusy_Button.Click += new System.EventHandler(this.SetBusy_Button_Click);
            // 
            // Alerts_Button
            // 
            this.Alerts_Button.Location = new System.Drawing.Point(392, 9);
            this.Alerts_Button.Name = "Alerts_Button";
            this.Alerts_Button.Size = new System.Drawing.Size(75, 23);
            this.Alerts_Button.TabIndex = 56;
            this.Alerts_Button.Text = "Alerts";
            this.Alerts_Button.UseVisualStyleBackColor = true;
            this.Alerts_Button.Click += new System.EventHandler(this.Alerts_Button_Click);
            // 
            // ContentSharing_Form
            // 
            this.AutoScaleDimensions = new System.Drawing.SizeF(6F, 13F);
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
            this.ClientSize = new System.Drawing.Size(485, 728);
            this.Controls.Add(this.Alerts_Button);
            this.Controls.Add(this.SetBusy_Button);
            this.Controls.Add(this.SharingInvitation_Groupbox);
            this.Controls.Add(this.ContentItem_GroupBox);
            this.Controls.Add(this.ContentBin_Groupbox);
            this.Controls.Add(this.StartConversation_Group);
            this.Controls.Add(this.ClientStateString_Label);
            this.Controls.Add(this.ClientState_Label);
            this.Name = "ContentSharing_Form";
            this.StartPosition = System.Windows.Forms.FormStartPosition.CenterScreen;
            this.Text = "Quick Meeting Console";
            this.FormClosing += new System.Windows.Forms.FormClosingEventHandler(this.ContentSharing_Form_FormClosing);
            this.Load += new System.EventHandler(this.ContentSharing_Form_Load);
            this.ConversationActions_Group.ResumeLayout(false);
            this.StartConversation_Group.ResumeLayout(false);
            this.StartConversation_Group.PerformLayout();
            this.ContentBin_Groupbox.ResumeLayout(false);
            this.ContentBin_Groupbox.PerformLayout();
            this.groupBox3.ResumeLayout(false);
            this.groupBox3.PerformLayout();
            this.groupBox2.ResumeLayout(false);
            this.groupBox1.ResumeLayout(false);
            this.ContentItem_GroupBox.ResumeLayout(false);
            this.ContentItem_GroupBox.PerformLayout();
            this.SharingInvitation_Groupbox.ResumeLayout(false);
            this.ResumeLayout(false);
            this.PerformLayout();

        }

        #endregion

        private System.Windows.Forms.Label ClientState_Label;
        private System.Windows.Forms.Label ClientStateString_Label;
        private System.Windows.Forms.ListBox Contact_ListBox;
        private System.Windows.Forms.GroupBox ConversationActions_Group;
        private System.Windows.Forms.Button EndConversation_Button;
        private System.Windows.Forms.Button Start_Button;
        private System.Windows.Forms.Label ContactList_Label;
        private System.Windows.Forms.ListBox Content_Listbox;
        private System.Windows.Forms.Label label1;
        private System.Windows.Forms.TextBox ShareableContentTitle_Textbox;
        private System.Windows.Forms.Button ShareWhiteboard_Button;
        private System.Windows.Forms.Button ContentShare_Button;
        private System.Windows.Forms.Button StopSharingContent_Button;
        private System.Windows.Forms.OpenFileDialog PickContentItemPath_OpenFileDialog;
        private System.Windows.Forms.Button PickAPowerPoint_Button;
        private System.Windows.Forms.Button PickNativeFile_Button;
        private System.Windows.Forms.Button DownloadAttachment_Button;
        private System.Windows.Forms.Button Accept_Button;
        private System.Windows.Forms.Button Reject_Button;
        private System.Windows.Forms.Panel ModalityConnectedState_Panel;
        private System.Windows.Forms.Label ActiveContent_Label;
        private System.Windows.Forms.Button ClearAnnotations_Button;
        private System.Windows.Forms.Button SaveAnnotations_Button;
        private System.Windows.Forms.Button SyncWithPresenter_Button;
        private System.Windows.Forms.Button TakeOverAsPresenter_Button;
        private System.Windows.Forms.Button GoBack_Button;
        private System.Windows.Forms.Button GoForward_Button;
        private System.Windows.Forms.GroupBox StartConversation_Group;
        private System.Windows.Forms.GroupBox ContentBin_Groupbox;
        private System.Windows.Forms.Label ModalityState_Label;
        private System.Windows.Forms.GroupBox ContentItem_GroupBox;
        private System.Windows.Forms.GroupBox SharingInvitation_Groupbox;
        private System.Windows.Forms.Button RemoveFromBin_Button;
        private System.Windows.Forms.Button AddPowerPoint_Button;
        private System.Windows.Forms.Button AddNativeFile_Button;
        private System.Windows.Forms.GroupBox groupBox2;
        private System.Windows.Forms.GroupBox groupBox1;
        private System.Windows.Forms.GroupBox groupBox3;
        private System.Windows.Forms.Button RefreshContent_Button;
        private System.Windows.Forms.Label label2;
        private System.Windows.Forms.FolderBrowserDialog DownloadFolderBrowser_FolderBrowser;
        private System.Windows.Forms.Button SetBusy_Button;
        private System.Windows.Forms.Button Alerts_Button;
    }
}
```

The following example is the interaction logic for the previous window declaration.

```csharp
using System;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;
using Microsoft.Lync.Model.Conversation;
using Microsoft.Lync.Model.Conversation.Sharing;
using System.Collections.Generic;
using System.Runtime.InteropServices;
using System.IO;

namespace ContentSharing
{
    public partial class ContentSharing_Form : Form
    {
        #region class field declarations

        /// <summary>
        /// The Application sharing modality of a remote presenting participant.
        /// </summary>
        ContentSharingModality _RemoteParticipantSharingModality;

        /// <summary>
        /// The new shareable content object created by the user.
        /// </summary>
        ShareableContent _ShareableContent;

        /// <summary>
        /// The file name and path of the PowerPoint deck to upload.
        /// </summary>
        string _PowerPointDeckName = string.Empty;

        /// <summary>
        /// Lync client platform. The entry point to the API
        /// </summary>
        Microsoft.Lync.Model.LyncClient _LyncClient;

        /// <summary>
        /// Represents a Lync conversation
        /// </summary>
        Conversation _conversation;

        /// <summary>
        /// Dictionary of all contacts selected from the multi-select enabled contact list on 
        /// UI
        /// </summary>
        Dictionary<string, Contact> _selectedContacts = new Dictionary<string, Contact>();

        /// <summary>
        /// The file name and path of a native file to upload.
        /// </summary>
        string _NativeFileNameAndPath = string.Empty;

        /// <summary>
        /// The file name of a native file to upload.
        /// </summary>
        string _NativeFileName = string.Empty;

        #endregion

        #region demo methods

        /// <summary>
        /// Ask user to select a PowerPoint slide deck to be uploaded
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void PickAPowerPoint_Button_Click(object sender, EventArgs e)
        {
            PickContentItemPath_OpenFileDialog.Title = "Choose a PowerPoint deck";
            PickContentItemPath_OpenFileDialog.RestoreDirectory = true;
            if (PickContentItemPath_OpenFileDialog.ShowDialog() == System.Windows.Forms.DialogResult.OK)
            {
                _PowerPointDeckName = PickContentItemPath_OpenFileDialog.FileName;
            }
        }

        /// <summary>
        /// 
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void AddPowerPoint_Button_Click(object sender, EventArgs e)
        {
            if (((Modality)_conversation.Modalities[ModalityTypes
            .ContentSharing]).State == ModalityState.Disconnected)
            {
                ConnectCSM();

            }
            else
            {
                if (!((Modality)_conversation.Modalities[ModalityTypes.ContentSharing])
                    .CanInvoke(ModalityAction.CreateShareablePowerPointContent))
                {
                    return;
                }

                if (_PowerPointDeckName.Length > 0)
                {
                    try
                    {

                        ContentSharingModality c = ((ContentSharingModality)_conversation
                            .Modalities[ModalityTypes.ContentSharing]);

                        string pptTitle = string.Empty;
                        Int32 lastWhack = _PowerPointDeckName.LastIndexOf(@"\");

                        //Strip off PowerPoint deck path, leaving only the file name to 
                        //be assigned as the ShareableContent.Title property
                        pptTitle = _PowerPointDeckName.Substring(
                            lastWhack + 1, _PowerPointDeckName.Length - (lastWhack + 1));

                        c.BeginCreateContentFromFile(
                            ShareableContentType.PowerPoint,
                            pptTitle,
                            _PowerPointDeckName,
                            false,
                            CreateShareableContentCallback,
                            c);

                    }
                    catch (InvalidStateException)
                    {
                        MessageBox.Show("Invalid state exception on BeginCreateContent ");
                    }
                    catch (NotInitializedException)
                    {
                        MessageBox.Show("Not initialized exception on BeginCreateContent ");
                    }
                    finally
                    {
                        //Clear the powerpoint deck name. The name will be filled again by 
                        //the user when they choose another deck to upload.
                        _PowerPointDeckName = null;
                    }
                }
            }
        }

        /// <summary>
        /// Connect the conversation ContentSharingModality the first time the user
        /// tries to upload a shareable content item
        /// </summary>
        private void ConnectCSM()
        {
            if (((Modality)_conversation.Modalities[ModalityTypes.ContentSharing])
            .CanInvoke(ModalityAction.Connect))
            {
                try
                {
                    ((Modality)_conversation.Modalities[ModalityTypes.ContentSharing]).
                        BeginConnect((ar) =>
                        {
                            ((Modality)_conversation.Modalities[ModalityTypes.ContentSharing]).
                                EndConnect(ar);
                        }
                        , null);
                }
                catch (OperationException oe)
                {
                    Console.WriteLine("Operation exception " + oe.Message);
                }
            }
        }

        /// <summary>
        /// Raised when the availability of an action on the content sharing modality changes
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ActionAvailabilityChanged(
            object sender, ModalityActionAvailabilityChangedEventArgs e)
        {
            AddAListItemDelegate EventLogger = new AddAListItemDelegate(AddAListItem);

            ContentSharingModality csm = ((ContentSharingModality)_conversation
                               .Modalities[ModalityTypes.ContentSharing]);

            EnableDisableButtonDelegate d = new EnableDisableButtonDelegate(EnableDisableButton);
            switch (e.Action)
            {
                case ModalityAction.CreateShareableNativeFileOnlyContent:
                    if (e.IsAvailable == false)
                        return;

                    if (_NativeFileName.Length == 0 || _NativeFileNameAndPath.Length == 0)
                    {
                        return;
                    }
                    UploadAFile();
                    break;
                case ModalityAction.CreateShareablePowerPointContent:
                    //If the user has chosen a PowerPoint deck to upload, then create 
                    //and upload it when the action is available
                    if (_PowerPointDeckName.Length > 0)
                    {
                        try
                        {
                            string pptTitle = string.Empty;
                            Int32 lastWhack = _PowerPointDeckName.LastIndexOf(@"\");

                            //Strip off PowerPoint deck path, leaving only the file name to 
                            //be assigned as the ShareableContent.Title property
                            pptTitle = _PowerPointDeckName.Substring(
                                lastWhack + 1
                                , _PowerPointDeckName.Length - (lastWhack + 1));

                            csm.BeginCreateContentFromFile(
                                ShareableContentType.PowerPoint,
                                pptTitle,
                                _PowerPointDeckName,
                                false,
                                (ar) =>
                                {
                                    try
                                    {
                                        ShareableContent sContent;
                                        sContent = csm.EndCreateContentFromFile(ar);
                                        _PowerPointDeckName = string.Empty;
                                        sContent.Upload();
                                    }
                                    catch (MaxContentsExceededException)
                                    {
                                        MessageBox.Show(
                                            "The meeting content bin is full. PowerPoint deck "
                                            + "cannot be uploaded");
                                    }
                                    catch (ContentTitleExistException)
                                    {
                                        MessageBox.Show(
                                            "The meeting content bin already contains an item "
                                            + "with this title. PowerPoint deck cannot be uploaded");
                                    }
                                    catch (ContentTitleInvalidException)
                                    {
                                        MessageBox.Show(
                                            "The whiteboard title is invalid. PowerPoint deck"
                                            + " cannot be uploaded");
                                    }
                                }
                                , null);

                        }
                        catch (InvalidStateException) { }
                        catch (NotInitializedException) { }
                        finally
                        {
                            //Clear the powerpoint deck name. The name will be filled again 
                            //by the user when they choose another deck to upload.
                            _PowerPointDeckName = null;
                        }
                    }

                    
                    break;
                case ModalityAction.CreateShareableWhiteboardContent:
                    if (csm.CanInvoke(
                        ModalityAction.CreateShareableWhiteboardContent))
                    {
                        csm.BeginCreateContent(
                            ShareableContentType.Whiteboard
                            , ShareableContentTitle_Textbox.Text,
                            (ar) =>
                            {
                                try
                                {
                                    ShareableContent sContent = csm.EndCreateContent(ar);
                                    sContent.Upload();
                                }
                                catch (MaxContentsExceededException)
                                {
                                    MessageBox.Show(
                                        "The meeting content bin is full. Whiteboard cannot be "
                                        + "uploaded");
                                }
                                catch (ContentTitleExistException)
                                {
                                    MessageBox.Show(
                                        "The meeting content bin already contains an item with "
                                        + "this title. Whiteboard cannot be uploaded");
                                }
                                catch (ContentTitleInvalidException)
                                {
                                    MessageBox.Show(
                                        "The whiteboard title is invalid. Whiteboard cannot "
                                        + "be uploaded");
                                }
                            }
                        , null);

                        //Clear the whiteboard title entry field
                        this.Invoke(
                            new ChangeControlTextDelegate(ChangeControlText)
                            , new object[] { ShareableContentTitle_Textbox, "" });
                    }

                    break;
                case ModalityAction.Accept:
                    _RemoteParticipantSharingModality = (ContentSharingModality)sender;
                    this.Invoke(d, new object[] { Accept_Button, e.IsAvailable });
                    break;
                case ModalityAction.Reject:
                    this.Invoke(d, new object[] { Reject_Button, e.IsAvailable });
                    break;
            }
        }

        /// <summary>
        /// Raised when an item is added to the content bin
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ContentAdded(object sender, ContentCollectionChangedEventArgs e)
        {
            AddAListItemDelegate ListAdder = new AddAListItemDelegate(AddAListItem);

            string newItem = string.Empty;
            e.Item.ActionAvailabilityChanged += _ShareableContent_ActionAvailabilityChanged;
            newItem = e.Item.Type.ToString() + "-" + e.Item.Title;
            this.Invoke(ListAdder, new object[] { Content_Listbox, newItem });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton)
                , new object[] { ContentShare_Button, true });
        }

        /// <summary>
        /// Places a selected content bin item on the sharing stage for presentation
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void ContentShare_Button_Click(object sender, EventArgs e)
        {
            string selectedItem = (string)Content_Listbox.SelectedItem;
            foreach (ShareableContent sContent in ((ContentSharingModality)_conversation
                .Modalities[ModalityTypes.ContentSharing]).ContentCollection)
            {
                if (sContent.Type.ToString() + "-" + sContent.Title == selectedItem)
                {
                    int hrReason;
                    if (sContent.CanInvoke(ShareableContentAction.Present, out hrReason))
                    {
                        _ShareableContent = sContent;
                        sContent.Present();
                    }
                    else
                    {
                        MessageBox.Show(
                            "Cannot present "
                            + sContent.Type.ToString()
                            + ": "
                            + hrReason.ToString());
                    }
                    break;
                }
            }
        }

        /// <summary>
        /// Return to meeting view of presented PowerPoint deck
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void SyncWithPresenter_Button_Click(object sender, EventArgs e)
        {
            try
            {
                ShareableContent shareableContent = ((ContentSharingModality)_conversation
                    .Modalities[ModalityTypes.ContentSharing]).ActiveContent;

                if (shareableContent.Type == ShareableContentType.PowerPoint)
                {
                    PowerPointContent ppc = shareableContent as PowerPointContent;
                    int dr;
                    if (ppc.CanInvoke(ShareableContentAction.SyncWithPresenter, out dr))
                    {
                        if (ppc.IsInSyncWithPresenter == false)
                        {
                            ppc.SyncWithPresenter();
                        }
                        else
                        {
                            MessageBox.Show("You are in sync with presenter");
                        }
                    }
                }
            }
            catch (InvalidOperationException ioe)
            {
                Console.WriteLine("Invalid operation " + ioe.Message);
            }
            catch (COMException c)
            {
                Console.WriteLine("COMException " + c.Message);
            }
            catch (Exception ex)
            {
                Console.WriteLine("Exception " + ex.Message);
            }
        }

        /// <summary>
        /// Take over as presenter of the shared content
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void TakeOverAsPresenter_Button_Click(object sender, EventArgs e)
        {
            ShareableContent activeContent = ((ContentSharingModality)_conversation
                    .Modalities[ModalityTypes.ContentSharing]).ActiveContent;

            if (activeContent != null)
            {
                int dr;
                if (activeContent.CanInvoke(ShareableContentAction.TakeOverAsPresenter, out dr))

                {
                    activeContent.TakeOverAsPresenter();
                }
            }
        }

        /// <summary>
        /// Scroll forward one slide in PowerPoint deck
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void GoForward_Button_Click_1(object sender, EventArgs e)
        {
            try
            {
                ShareableContent shareableContent = ((ContentSharingModality)_conversation
                    .Modalities[ModalityTypes.ContentSharing]).ActiveContent;

                if (shareableContent.Type == ShareableContentType.PowerPoint)
                {
                    PowerPointContent ppc = shareableContent as PowerPointContent;
                    ppc.GoForward();
                }
            }
            catch (InvalidOperationException ioe)
            {
                Console.WriteLine("Cannot scroll PowerPoint deck forward " + ioe.Message);
            }
        }

        /// <summary>
        /// Scroll back one slide in PowerPoint deck
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void GoBack_Button_Click_1(object sender, EventArgs e)
        {
            try
            {
                ShareableContent shareableContent = ((ContentSharingModality)_conversation
                    .Modalities[ModalityTypes.ContentSharing]).ActiveContent;
                if (shareableContent.Type == ShareableContentType.PowerPoint)
                {
                    PowerPointContent ppc = shareableContent as PowerPointContent;
                    ppc.GoBackward();
                }
            }
            catch (InvalidOperationException ioe)
            {
                Console.WriteLine("Cannot scroll PowerPoint deck back " + ioe.Message);
            }
        }

        /// <summary>
        /// Removes a presented content item from the sharing stage
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void StopSharingContent_Button_Click(object sender, EventArgs e)
        {
            ContentSharingModality csm = (ContentSharingModality)_conversation
            .Modalities[ModalityTypes.ContentSharing];

            int hrReason;
            if (csm.ActiveContent.CanInvoke(ShareableContentAction.StopPresenting, out hrReason))
            {
                csm.ActiveContent.StopPresenting();
            }
            else
            {
                MessageBox.Show(
                    "Cannot stop presenting "
                    + csm.ActiveContent.Type.ToString()
                    + ": " + hrReason.ToString());
            }
        }

        /// <summary>
        /// As of Beta 1 refresh, ClearAllAnnotations is not implemented.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void ClearAnnotations_Button_Click(object sender, EventArgs e)
        {
            ContentSharingModality csm =
            (ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing];

            int hrReason;
            if (csm.ActiveContent.CanInvoke(
                ShareableContentAction.ClearAllAnnotations, out hrReason))
            {
                csm.ActiveContent.ClearAllAnnotations();
            }
        }

        /// <summary>
        /// Un-registers event handlers for all conversation objects and ends the conversation
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void EndConversation_Button_Click(object sender, EventArgs e)
        {
            if (_conversation == null)
            {
                return;
            }
            if (_conversation.State != ConversationState.Terminated)
            {
                //Clean up all conversation object registration so that events do not fire
                //on conversation objects as they are being nulled by the platform when the
                //conversation terminates.

                ContentSharingModality contentModality = (ContentSharingModality)_conversation
                    .Modalities[ModalityTypes.ContentSharing];

                _conversation.ParticipantAdded -= _conversation_ParticipantAdded;
                _conversation.ParticipantRemoved -= _conversation_ParticipantRemoved;
                contentModality.ModalityStateChanged -= Modality_ModalityStateChanged;
                contentModality.ActionAvailabilityChanged -= _sharingModality_ActionAvailabilityChanged;
                contentModality.ActiveContentChanged -= _sharingModality_ActiveContentChanged;
                contentModality.ContentAdded -= _sharingModality_ContentAdded;
                contentModality.ContentRemoved -= _sharingModality_ContentRemoved;

                foreach (Participant p in _conversation.Participants)
                {
                    ((Modality)p.Modalities[ModalityTypes.ContentSharing])
                        .ActionAvailabilityChanged -= _sharingModality_ActionAvailabilityChanged;
                }
                _conversation.End();
            }
        }

        /// <summary>
        /// User selects a content bin item. Check for the availability of an action 
        /// on the selected content.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Content_Listbox_SelectedIndexChanged(object sender, EventArgs e)
        {
            ListBox list = (ListBox)sender;
            ContentShare_Button.Enabled = false;
            string selectedItem = (string)list.SelectedItem;
            foreach (ShareableContent sContent in ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).ContentCollection)
            {
                if (sContent.Type.ToString() + "-" + sContent.Title == selectedItem)
                {
                    int hrReason;
                    switch (sContent.Type)
                    { 
                        case ShareableContentType.NativeFile:
                            if (sContent.CanInvoke(ShareableContentAction.DownloadFile, out hrReason))
                            {
                                DownloadAttachment_Button.Enabled = true;
                            }
                            break;
                        case ShareableContentType.PowerPoint:
                            if (sContent.CanInvoke(ShareableContentAction.DownloadFile, out hrReason))
                            {
                                DownloadAttachment_Button.Enabled = true;
                            }
                            ContentShare_Button.Enabled = false;
                            if (sContent.CanInvoke(ShareableContentAction.Present, out hrReason))
                            {
                                ContentShare_Button.Enabled = true;
                            }

                            StopSharingContent_Button.Enabled = false;
                            if (sContent.CanInvoke(ShareableContentAction.StopPresenting, out hrReason))
                            {
                                StopSharingContent_Button.Enabled = true;
                            }
                            break;
                        case ShareableContentType.Whiteboard:
                            ContentShare_Button.Enabled = false;
                            if (sContent.CanInvoke(ShareableContentAction.Present, out hrReason))
                            {
                                ContentShare_Button.Enabled = true;
                            }

                            StopSharingContent_Button.Enabled = false;
                            if (sContent.CanInvoke(ShareableContentAction.StopPresenting, out hrReason))
                            {
                                StopSharingContent_Button.Enabled = true;
                            }
                            break;
                    }
                    break;
                }
            }
        }
        #endregion

        #region UI event handlers

        /// <summary>
        /// Creates and uploads a whiteboard session
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void ShareNewContent_Button_Click(object sender, EventArgs e)
        {
            ContentSharingModality csm = (ContentSharingModality)_conversation
            .Modalities[ModalityTypes.ContentSharing];
            if (csm.State == ModalityState.Disconnected)
            {
                ConnectCSM();
            }
            else
            {
                if (csm.CanInvoke(ModalityAction.CreateShareableWhiteboardContent))
                {
                    csm.BeginCreateContent(
                        ShareableContentType.Whiteboard
                        , ShareableContentTitle_Textbox.Text
                        , (ar) =>
                        {
                            try
                            {
                                ShareableContent sContent = csm.EndCreateContent(ar);
                                sContent.Upload();
                            }
                            catch (MaxContentsExceededException)
                            {
                                MessageBox.Show(
                                    "The meeting content bin is full. Whiteboard "
                                    + "cannot be uploaded");
                            }
                            catch (ContentTitleExistException)
                            {
                                MessageBox.Show(
                                    "The meeting content bin already contains an item "
                                    + "with this title. Whiteboard cannot be uploaded");
                            }
                            catch (ContentTitleInvalidException)
                            {
                                MessageBox.Show(
                                    "The whiteboard title is invalid. Whiteboard cannot "
                                    + "be uploaded");
                            }
                        }
                    , null);

                    //Clear the whiteboard title string entry field
                    ShareableContentTitle_Textbox.Text = string.Empty;
                }
            }
        }

        /// <summary>
        /// If content stage item is a Whiteboard, saves whiteboard annotations.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void SaveAnnotations_Button_Click(object sender, EventArgs e)
        {
            ContentSharingModality csm = (ContentSharingModality)_conversation
            .Modalities[ModalityTypes.ContentSharing];

            if (csm.ActiveContent.Type != ShareableContentType.Whiteboard)
            {
                return;
            }

            int hrReason;
            if (csm.ActiveContent.CanInvoke(ShareableContentAction.SaveAnnotation, out hrReason))
            {
                csm.ActiveContent.SaveAnnotation(
                    @"c:\users\public\"
                    + csm.ActiveContent.Title
                    + ".png"
                    , ContentSavingFileType.PNG);

                //Get a FileInfo object that wraps the downloaded file
                FileInfo file = new FileInfo(
                    @"c:\users\public\"
                    + csm.ActiveContent.Title
                    + ".png");

                //If the file was downloaded then give the user the download path
                //and file name
                if (file.Exists)
                {
                    MessageBox.Show(
                        "Annotations have been saved at "
                        + file.Directory.FullName + @"\"
                        + csm.ActiveContent.Title + ".png");
                }
            }
            else
            {
                MessageBox.Show("Annotations cannot be saved for " + _ShareableContent.Title);
            }
        }

        /// <summary>
        /// Accepts an invitation to share meeting content
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Accept_Button_Click(object sender, EventArgs e)
        {
            if (_RemoteParticipantSharingModality.CanInvoke(ModalityAction.Accept))
            {
                _RemoteParticipantSharingModality.Accept();
            }
        }

        /// <summary>
        /// invoked when sample form is loaded. Initializes fields, gets API entry point, 
        /// registers for events on Lync Client and ConversationManager.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void ContentSharing_Form_Load(object sender, EventArgs e)
        {
            try
            {
                //Get the API entry point
                _LyncClient = LyncClient.GetClient();

                //Resource sharing is not supported in UI suppression mode. Sample closes
                //if Lync UI is suppressed
                if (_LyncClient.InSuppressedMode == true)
                {
                    MessageBox.Show(
                        "Lync Client is in UI Suppressed mode. Sharing is not supported.",
                        "Application Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                    this.Close();
                }

                _LyncClient.Self.Contact.ContactInformationChanged += new EventHandler<ContactInformationChangedEventArgs>(Contact_ContactInformationChanged);

                //Display the current state of the Lync client.
                ClientStateString_Label.Text = _LyncClient.State.ToString();

                //If the Lync client is signed out, sign into the Lync client
                if (_LyncClient.State == ClientState.SignedOut)
                {
                    _LyncClient.EndSignIn(_LyncClient.BeginSignIn(
                        "terrya@contoso.com",
                        "terrya@contoso.com",
                        "MyPassword",
                        null,
                        null));
                }

                //Display the current state of the Lync client.
                ClientStateString_Label.Text = _LyncClient.State.ToString();

                //Register for the three Lync client events needed so that application is 
                //notified when:
                // * Lync client signs in or out
                // * A new conversation is added (remotely via invite or locally by user)
                // * A conversation is removed (conversation ends)
                _LyncClient.StateChanged += _LyncClient_StateChanged;
                _LyncClient.ConversationManager.ConversationAdded +=
                    ConversationManager_ConversationAdded;
                _LyncClient.ConversationManager.ConversationRemoved +=
                    ConversationManager_ConversationRemoved;

                //Enable the start conversation button on the UI
                Start_Button.Enabled = true;

                //ShareDesktop.LoadAllContacts loads the contact list on the UI with 
                //all contacts that are in the user's Lync client contact list.
                LoadAllContacts();

            }
            catch (NotInitializedException)
            {
                MessageBox.Show(
                    "Client is not initialized.  Closing form",
                    "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
            catch (ClientNotFoundException)
            {
                MessageBox.Show(
                    "Client is not running.  Closing form",
                    "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
            catch (Exception exc)
            {
                MessageBox.Show(
                    "General exception: " + exc.Message,
                    "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
        }

        void Contact_ContactInformationChanged(object sender, ContactInformationChangedEventArgs e)
        {
           // MessageBox.Show("Contact information changed " + e.ChangedContactInformation.ToString());
        }

        /// <summary>
        /// Starts a new conversation
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Start_Button_Click(object sender, EventArgs e)
        {
            if (_conversation == null)
            {
                Contact aContact;
                foreach (Object selectedObject in Contact_ListBox.SelectedItems)
                {
                    aContact = _LyncClient.ContactManager.GetContactByUri(
                        selectedObject.ToString());

                    if (!_selectedContacts.ContainsKey(selectedObject.ToString()))
                    {
                        _selectedContacts.Add(selectedObject.ToString(), aContact);
                    }
                }
                _conversation = _LyncClient.ConversationManager.AddConversation();

            }
        }
        
        /// <summary>
        /// Downloads an attachment or powerpoint from meeting
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void DownloadAttachment_Button_Click(object sender, EventArgs e)
        {
            //get title of selected content to be downloaded
            string selectedItem = (string)Content_Listbox.SelectedItem;

            //get path to download
            string downloadPath = string.Empty;
            DownloadFolderBrowser_FolderBrowser.Description =
                "Pick a meeting content download folder";
            if (DownloadFolderBrowser_FolderBrowser.ShowDialog() ==
                System.Windows.Forms.DialogResult.OK)
            {
                downloadPath = DownloadFolderBrowser_FolderBrowser.SelectedPath;
            }

            //Get each native file attachment and then download it
            ShareableContent contentToDownload = null;
            foreach (ShareableContent sContent in ((ContentSharingModality)_conversation.
                Modalities[ModalityTypes.ContentSharing]).ContentCollection)
            {
                if (sContent.Type + "-" + sContent.Title == selectedItem)
                {
                    contentToDownload = sContent;
                    break;
                }
            }

            if (contentToDownload != null)
            {
                string downloadFileTitle = string.Empty;
                if (contentToDownload.Title.Length != 0)
                {
                    downloadFileTitle = contentToDownload.Title;
                }
                else
                {
                    downloadFileTitle = contentToDownload.Properties[ShareableContentProperty.
                        Title].ToString();
                }
                int hr;
                if (contentToDownload.CanInvoke(ShareableContentAction.DownloadFile, out hr))
                {
                    contentToDownload.BeginDownloadFile(
                        downloadPath + @"\" + downloadFileTitle, (ar) =>
                        {
                            MessageBox.Show("Downloaded file: " +
                                contentToDownload.EndDownloadFile(ar));
                        }
                    , null);
                }
            }
        }

        private void PickNativeFile_Button_Click(object sender, EventArgs e)
        {
            PickContentItemPath_OpenFileDialog.RestoreDirectory = true;
            PickContentItemPath_OpenFileDialog.Title = "Choose a native file";
            PickContentItemPath_OpenFileDialog.FileName = "*.*";
            if (PickContentItemPath_OpenFileDialog.ShowDialog() == System.Windows.Forms.
                DialogResult.OK)
            {
                _NativeFileNameAndPath = PickContentItemPath_OpenFileDialog.FileName;
                _NativeFileName = PickContentItemPath_OpenFileDialog.SafeFileName;
            }

        }

        private void UploadNativeFile_Button_Click(object sender, EventArgs e)
        {
            if (_NativeFileName.Length == 0 || _NativeFileNameAndPath.Length == 0)
            {
                return;
            }
            if (((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).
                State == ModalityState.Connected)
            {
                UploadAFile();
            }
            else
            {
                ConnectCSM();
            }
        }

        private void Reject_Button_Click(object sender, EventArgs e)
        {
            if (_RemoteParticipantSharingModality.CanInvoke(ModalityAction.Reject))
            {
                _RemoteParticipantSharingModality.Reject(ModalityDisconnectReason.Decline);
            }
        }

        private void ContentSharing_Form_FormClosing(object sender, FormClosingEventArgs e)
        {
            if (_conversation == null)
            {
                return;
            }
            if (_conversation.State != ConversationState.Terminated)
            {
                _conversation.End();
            }
        }

        #endregion

        #region Client event handlers

        /// <summary>
        /// Handles the event raised when a user signs in to or out of the Lync client.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _LyncClient_StateChanged(object sender, ClientStateChangedEventArgs e)
        {
            //If the client has signed in then get the client's contact list and enable the conversation start button.
            if (e.NewState == ClientState.SignedIn)
            {
                this.Invoke(new LoadAllContactsDelegate(LoadAllContacts));
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, true });
            }
            else
            {
                this.Invoke(new ClearAllContactsDelegate(ClearAllContacts));
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, false });

                this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { ClientStateString_Label, e.NewState.ToString() });
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { EndConversation_Button, false });
            }
        }
        #endregion

        #region conversation manager event handlers

        /// <summary>
        /// Handles the event raised when a new conversation is added. This sample only hosts 
        /// one conversation at a time. Once this event is handled, the sample un-registers 
        /// for this event. The event is registered again when this conversation is removed 
        /// from the ContactManager.Conversations collection upon termination of this 
        /// conversation.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ConversationManager_ConversationAdded(
            object sender, Microsoft.Lync.Model.Conversation.ConversationManagerEventArgs e)
        {
            if (IsShadowConversation(e.Conversation))
            {
                return;
            }

            if (e.Conversation != _conversation)
            {
                return;
            }

            //Register for participant added events on the new conversation
            _conversation.ParticipantAdded += _conversation_ParticipantAdded;
            _conversation.ParticipantRemoved += _conversation_ParticipantRemoved;
            _conversation.StateChanged += new EventHandler<ConversationStateChangedEventArgs>(_conversation_StateChanged);

            ((Modality)_conversation.Modalities[ModalityTypes.ContentSharing]).ModalityStateChanged
                += Modality_ModalityStateChanged;
            ((Modality)_conversation.Modalities[ModalityTypes.ContentSharing]).ActionAvailabilityChanged
                += _sharingModality_ActionAvailabilityChanged;

            ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).
                ActiveContentChanged += _sharingModality_ActiveContentChanged;

            ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).
                ContentAdded += _sharingModality_ContentAdded;

            ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).
                ContentRemoved += _sharingModality_ContentRemoved;

            //Iterate on the contact dictionary that is filled from the contact Sip addresses 
            //selected from the contact list UI control. Add each selected contact to the 
            //conversation, causing an invitation to be sent to each contact.
            if (_conversation.CanInvoke(ConversationAction.AddParticipant))
            {
                foreach (Contact selectedContact in _selectedContacts.Values)
                {
                    Participant newParticipant = _conversation.AddParticipant(selectedContact);

                }
            }

            ((InstantMessageModality)_conversation.Modalities[ModalityTypes.InstantMessage]).
            BeginSendMessage(
            "Hello. I would like to share something with you.",
            (ar) =>
            {
                try
                {
                    ((InstantMessageModality)_conversation.Modalities[ModalityTypes.InstantMessage]).EndSendMessage(ar);
                }
                catch (LyncClientException) { Console.WriteLine("Message could not be delivered"); }
            }
            , null);
        }

        void _conversation_StateChanged(object sender, ConversationStateChangedEventArgs e)
        {
            if (e.NewState == ConversationState.Active)
            {
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { EndConversation_Button, true });
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, false });
            }
            if (e.NewState == ConversationState.Terminated)
            {
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { EndConversation_Button, false });
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, true });
            }
        }

        
        
        /// <summary>
        /// Handles the event raised when the active conversation is terminated and removed from the collection of conversations
        /// on ConversationManager.Conversations
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ConversationManager_ConversationRemoved(object sender, ConversationManagerEventArgs e)
        {

            if (e.Conversation == _conversation)
            {
                this.Invoke(new SetContactSelectionModeDelegate(SetContactSelectionMode), new object[] { SelectionMode.MultiSimple });
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { EndConversation_Button, false });
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, true });
                this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { ContactList_Label, "People in Meeting" });
                this.Invoke(new LoadAllContactsDelegate(LoadAllContacts));
                this.Invoke(new ClearAllListItemsDelegate(ClearAllListItems), new object[] { Content_Listbox });
                this.Invoke(new ChangeControlBackgroundDelegate(ChangeControlBackground), new object[] { ModalityConnectedState_Panel, System.Drawing.Color.Red });

                //Un-register for participant events on the conversation that is terminated.
                _conversation.ParticipantAdded -= _conversation_ParticipantAdded;
                _conversation.ParticipantRemoved -= _conversation_ParticipantRemoved;
                _ShareableContent = null;

                //de-reference the class state
                _conversation = null;

                //Clear out the contact list on the UI to be replaced with only the contacts selected for the current conversation.
                this.Invoke(new LoadAllContactsDelegate(LoadAllContacts));
            }
        }

        #endregion

        #region Conversation event handlers

        /// <summary>
        /// Handles the participant added event. Registers for events on the application 
        /// sharing modality for the 
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _conversation_ParticipantAdded(
            object sender, ParticipantCollectionChangedEventArgs e)
        {
            //Register for event raised when a participant IMModality is connected to 
            //the conversation. 
            //Use this event to add participant to contact listbox
            ((Modality)e.Participant.Modalities[ModalityTypes.InstantMessage]).
                ModalityStateChanged += Participant_ModalityStateChanged;

            //Is this added participant the local user?
            if (!e.Participant.IsSelf)
            {
                //Event raised when content sharing action availability changes for a 
                //participant
                ((Modality)e.Participant.Modalities[ModalityTypes.ContentSharing]).
                    ActionAvailabilityChanged += _sharingModality_ActionAvailabilityChanged;
            }
        }

        /// <summary>
        /// Handles the event raised when a particpant is removed from the conversation.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _conversation_ParticipantRemoved(object sender, ParticipantCollectionChangedEventArgs e)
        {
            this.Invoke(new RemoveAContactDelegate(RemoveAContact), new object[] { e.Participant.Contact.Uri});
        }
        #endregion

        #region participant event handlers
        /// <summary>
        /// Raised when the state of a participant's IM modality changes
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Participant_ModalityStateChanged(Object sender, ModalityStateChangedEventArgs e)
        {
            //Modality will be connected for each particpant whethere they have accepted the 
            //shariing invite or not.
            if (sender.GetType().Name == "InstantMessageModality")
            {
                if (e.NewState == ModalityState.Connected)
                {
                    InstantMessageModality IMModality = sender as InstantMessageModality;
                    this.Invoke(
                        new AddAContactDelegate(AddAContact),
                        new object[] { IMModality.Participant.Contact.Uri });
                }
            }
        }
        #endregion

        #region application sharing modality event handlers

        /// <summary>
        /// Handles the even raised when the state of an application sharing modality changes.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Modality_ModalityStateChanged(object sender, ModalityStateChangedEventArgs e)
        {
            //Modality will be connected for each particpant whethere they have accepted 
            //the shariing invite or not.

            switch (sender.GetType().Name)
            {
                case "ContentSharingModality":
                    ContentSharingModality thisModality = sender as ContentSharingModality;
                    if (thisModality == ((ContentSharingModality)_conversation.
                        Modalities[ModalityTypes.ContentSharing]))
                    {
                        switch (e.NewState)
                        {
                            case ModalityState.Connecting:
                                this.Invoke(
                                    new ChangeControlBackgroundDelegate(
                                        ChangeControlBackground),
                                        new object[] { ModalityConnectedState_Panel, 
                                            System.Drawing.Color.Gold });
                                break;
                            case ModalityState.Connected:
                                this.Invoke(
                                    new ChangeControlBackgroundDelegate(
                                        ChangeControlBackground),
                                        new object[] { ModalityConnectedState_Panel, 
                                            System.Drawing.Color.Green });
                                this.Invoke(
                                    new EnableDisableButtonDelegate(EnableDisableButton),
                                    new object[] { ShareWhiteboard_Button, true });
                                break;
                            case ModalityState.Disconnected:
                                this.Invoke(
                                    new ChangeControlBackgroundDelegate(
                                        ChangeControlBackground),
                                        new object[] { 
                                            ModalityConnectedState_Panel, 
                                            System.Drawing.Color.Red });
                                break;
                        }
                    }
                    break;
            }
        }

        /// <summary>
        /// Raised when an item is removed from the content bin
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ContentRemoved(object sender, ContentCollectionChangedEventArgs e)
        {
            this.Invoke(new ClearAllListItemsDelegate(ClearAllListItems), new object[] { Content_Listbox});
            foreach (ShareableContent sc in ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).ContentCollection)
            {
                string newItem = sc.Type.ToString() + "-" + sc.Title;
                this.Invoke(new AddAListItemDelegate(AddAListItem), new object[] { Content_Listbox, newItem });
            }
        }

        /// <summary>
        /// Raised when one content bin item is moved off the sharing stage and is replaced by another
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ActiveContentChanged(object sender, ActiveContentChangedEventArgs e)
        {
            if (e.ActiveContent != null)
            {
                _ShareableContent = e.ActiveContent;
                this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { ActiveContent_Label, e.ActiveContent.Title });
                EnableDisableButtonDelegate d = new EnableDisableButtonDelegate(EnableDisableButton);
                if (e.ActiveContent.Type == ShareableContentType.PowerPoint)
                {
                    this.Invoke(d, new object[] { GoBack_Button, true });
                    this.Invoke(d, new object[] { GoForward_Button, true });
                    this.Invoke(d, new object[] { ClearAnnotations_Button, false });
                    Int32 hrReason;
                    if (e.ActiveContent.CanInvoke(ShareableContentAction.ClearAllAnnotations, out hrReason))
                    {
                        this.Invoke(d, new object[] { ClearAnnotations_Button, true });
                    }

                }
                else if (e.ActiveContent.Type == ShareableContentType.Whiteboard)
                {
                    Int32 hrReason;
                    if (e.ActiveContent.CanInvoke(ShareableContentAction.ClearAllAnnotations, out hrReason))
                    {
                        this.Invoke(d, new object[] { ClearAnnotations_Button, true });
                    }
                    if (e.ActiveContent.CanInvoke(ShareableContentAction.SaveAnnotation, out hrReason))
                    {
                        this.Invoke(d, new object[] { SaveAnnotations_Button, true });
                    }

                    this.Invoke(d, new object[] { GoBack_Button, false });
                    this.Invoke(d, new object[] { GoForward_Button, false });
                }
            }
        }
        #endregion

        #region Shareable Content Event Callback Methods

        /// <summary>
        /// Raised when the availability of an action on a ShareableContent object changes
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _ShareableContent_ActionAvailabilityChanged(object sender, ShareableContentActionAvailabilityChangedEventArgs e)
        {
            ShareableContent sContent = (ShareableContent)sender;

            EnableDisableButtonDelegate d = new EnableDisableButtonDelegate(EnableDisableButton);
            switch (e.Action)
            {
                case ShareableContentAction.SaveAnnotation:
                    this.Invoke(d, new object[] { SaveAnnotations_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.ClearAllAnnotations:
                    this.Invoke(d, new object[] { ClearAnnotations_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.SyncWithPresenter:
                    this.Invoke(d, new object[] { SyncWithPresenter_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.TakeOverAsPresenter:
                    this.Invoke(d, new object[] { TakeOverAsPresenter_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.StopPresenting:
                    this.Invoke(d, new object[] { StopSharingContent_Button, e.IsAvailable });
                    break;
                case ShareableContentAction.Present:
                    if (sContent.Owner != _LyncClient.Self.Contact)
                    {
                        this.Invoke(d, new object[] { SyncWithPresenter_Button, !e.IsAvailable });
                    }
                    break;
            }
        }
        
        #endregion

        #region API Operation callback methods
        private void CreateShareableContentCallback(System.IAsyncResult ar)
        {
            try
            {
                ContentSharingModality shareModality = (ContentSharingModality)ar.AsyncState;
                ShareableContent sContent;
                if (_PowerPointDeckName == string.Empty && _NativeFileNameAndPath == string.Empty)
                {
                    sContent = shareModality.EndCreateContent(ar);
                }
                else
                {
                    sContent = shareModality.EndCreateContentFromFile(ar);
                    _PowerPointDeckName = string.Empty;
                    _NativeFileNameAndPath = string.Empty;
                }
                sContent.Upload();
            }
            catch (MaxContentsExceededException) 
            {
                System.Diagnostics.Debug.WriteLine("Too many items in content bin");
            }
            catch (ContentTitleExistException) 
            {
                System.Diagnostics.Debug.WriteLine("Duplicate content title");
            }
            catch (ContentTitleInvalidException) 
            {
                System.Diagnostics.Debug.WriteLine("Invalid character in content title");
            }
        }

        #endregion

        #region UI update helper methods and their delegates
        private delegate void LoadAllContactsDelegate();

        /// <summary>
        /// Iterates on all groups and adds an Uri string for each contact in a group to a 
        /// list on the UI
        /// </summary>
        private void LoadAllContacts()
        {
            //Set the selection mode of the UI list to multi-select
            Contact_ListBox.SelectionMode = SelectionMode.MultiSimple;
            Contact_ListBox.Items.Clear();
            foreach (Group group in _LyncClient.ContactManager.Groups)
            {
                foreach (Contact contact in group)
                {
                    if (!Contact_ListBox.Items.Contains(contact.Uri))
                        Contact_ListBox.Items.Add(contact.Uri);
                }
            }
        }

        /// <summary>
        /// Filters out the "shadow" conversation that is created when a content sharing 
        /// modality is connected in a conversation when the user has Tabbed Conversations 
        /// enabled in the Lync UI
        /// </summary>
        /// <param name="newConversation"></param>
        /// <returns></returns>
        private Boolean IsShadowConversation(Conversation newConversation)
        {
            if (newConversation.SelfParticipant != null)
            {
                return false;
            }
            foreach (Modality m in newConversation.Modalities.Values)
            {
                if (m.State == ModalityState.Notified)
                {
                    return false;
                }
            }
            return true;
        }

        /// <summary>
        /// Creates a ShareableObject for selected native file and uploads the file
        /// </summary>
        private void UploadAFile()
        {
            try
            {
                if (((ContentSharingModality)_conversation.
                    Modalities[ModalityTypes.ContentSharing]).
                    CanInvoke(ModalityAction.CreateShareableNativeFileOnlyContent))
                {
                    ContentSharingModality contentSharingModality =
                        (ContentSharingModality)_conversation.
                        Modalities[ModalityTypes.ContentSharing];

                    contentSharingModality.BeginCreateContentFromFile(
                        ShareableContentType.NativeFile,
                        _NativeFileName,
                        _NativeFileNameAndPath,
                        true,
                        (ar) =>
                        {
                            ShareableContent sContent = contentSharingModality.
                                EndCreateContentFromFile(ar);
                            _PowerPointDeckName = string.Empty;
                            _NativeFileNameAndPath = string.Empty;
                            sContent.Upload();
                        }
                        , null);
                }
            }
            catch (InvalidStateException)
            {
                MessageBox.Show(
                    "Invalid state exception on BeginCreateContent ");
            }
            catch (NotInitializedException)
            {
                MessageBox.Show(
                    "Not initialized exception on BeginCreateContent ");
            }
            finally { _NativeFileNameAndPath = string.Empty; }

        }

        private delegate void EnableDisableButtonDelegate(Button buttonToUpdate, Boolean newButtonEnableState);

        /// <summary>
        /// Enables or disables a UI button based on the actionAvailability
        /// </summary>
        /// <param name="buttonToUpdate"></param>
        /// <param name="newButtonEnableState"></param>
        private void EnableDisableButton(Button buttonToUpdate, Boolean newButtonEnableState)
        {
            buttonToUpdate.Enabled = newButtonEnableState;
        }

        private delegate void ClearAllListItemsDelegate(ListBox boxToClear);
        private void ClearAllListItems(ListBox boxToClear)
        {
            boxToClear.Items.Clear();
        }

        private delegate void AddAListItemDelegate(ListBox listToAppend, object itemToAdd);
        private void AddAListItem(ListBox listToAppend, object itemToAdd)
        {
            if (!listToAppend.Items.Contains(itemToAdd))
            {
                listToAppend.Items.Add(itemToAdd);
            }
        }

        private delegate void RemoveListItemDelegate(ListBox listToTruncate, string itemToRemove);
        private void RemoveListItem(ListBox listToTruncate, string itemToRemove)
        {
            if (listToTruncate.Items.Contains(itemToRemove))
            {
                listToTruncate.Items.Remove(itemToRemove);
            }
        }
        private delegate void ClearAllContactsDelegate();
        private void ClearAllContacts()
        {
            Contact_ListBox.Items.Clear();
        }

        private delegate void AddAContactDelegate(string ContactUri);
        private void AddAContact(string ContactUri)
        {
            Contact_ListBox.SelectionMode = SelectionMode.One;
            if (!Contact_ListBox.Items.Contains(ContactUri))
            {
                Contact_ListBox.Items.Add(ContactUri);
            }
        }

        private delegate void RemoveAContactDelegate(string ContactUri);
        private void RemoveAContact(string ContactUri)
        {
            Contact_ListBox.Items.Remove(ContactUri);
        }

        private delegate void ChangeButtonTextDelegate(Button buttonToChange, string newText);
        private void ChangeButtonText(Button buttonToChange, string newText)
        {
            buttonToChange.Text = newText;
        }

        private delegate void SetContactSelectionModeDelegate(SelectionMode newMode);
        /// <summary>
        /// Changes the contact list on the UI from single-select to multi-select mode
        /// </summary>
        /// <param name="newMode"></param>
        private void SetContactSelectionMode(SelectionMode newMode)
        {
            Contact_ListBox.SelectionMode = newMode;
        }

        private delegate void ChangeLabelTextDelegate(Label labelToUpdate, string newText);
        /// <summary>
        /// Replaces the text of any label control on the UI with new text
        /// </summary>
        /// <param name="labelToUpdate"></param>
        /// <param name="newText"></param>
        private void ChangeLabelText(Label labelToUpdate, string newText)
        {
            labelToUpdate.Text = newText;
        }

        private delegate void ChangeControlTextDelegate(object controlToUpdate, string newText);

        /// <summary>
        /// Replaces the text property value with a new string
        /// </summary>
        /// <param name="controlToUpdate"></param>
        /// <param name="newText"></param>
        private void ChangeControlText(object controlToUpdate, string newText)
        {
            switch (controlToUpdate.GetType().Name)
            {
                case "TextBox":
                    TextBox updatedTextBox = controlToUpdate as TextBox;
                    updatedTextBox.Text = newText;
                    break;
                case "Button":
                    Button updatedButton = controlToUpdate as Button;
                    updatedButton.Text = newText;
                    break;
                case "Label":
                    Label updatedLabel = controlToUpdate as Label;
                    updatedLabel.Text = newText;
                    break;
            }
        }

        private delegate void ChangeControlBackgroundDelegate(Control controlToChange, System.Drawing.Color newColor);
        private void ChangeControlBackground(Control controlToChange, System.Drawing.Color newColor)
        {
            controlToChange.BackColor = newColor;
        }

        #endregion

        #region constructors
        public ContentSharing_Form()
        {
            InitializeComponent();
        }
        public ContentSharing_Form(Conversation newConversation)
        {
            InitializeComponent();
            _conversation = newConversation;
        }
        #endregion

        private void RemoveFromBin_Button_Click(object sender, EventArgs e)

        {
            string selectedItem = (string)Content_Listbox.SelectedItem;
            foreach (ShareableContent sContent in ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).ContentCollection)
            {
                if (sContent.Type.ToString() + "-" + sContent.Title == selectedItem)
                {
                    int hrReason;
                    if (sContent.CanInvoke(ShareableContentAction.Remove, out hrReason))
                    {
                        _ShareableContent = sContent;
                        sContent.ActionAvailabilityChanged -= _ShareableContent_ActionAvailabilityChanged;
                        sContent.Remove();
                    }
                    else
                    {
                        MessageBox.Show("Cannot remove " + selectedItem.ToString() +": " + hrReason.ToString());
                    }
                    break;
                }
            }
        }
        private void RefreshContent_Button_Click(object sender, EventArgs e)
        {
            Content_Listbox.Items.Clear();
            foreach (ShareableContent sc in ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).ContentCollection)
            {
                string newItem = string.Empty;
                newItem = sc.Type.ToString() + "-" + sc.Title;
                Content_Listbox.Items.Add(newItem);
            }
        }

        private void SetBusy_Button_Click(object sender, EventArgs e)
        {
            Dictionary<PublishableContactInformationType, object> publishableAvailablility = new Dictionary<PublishableContactInformationType, object>();
            ContactAvailability currentAvailability = (ContactAvailability) _LyncClient.Self.Contact.GetContactInformation(ContactInformationType.Availability);
            if (currentAvailability != ContactAvailability.DoNotDisturb)
            {
                publishableAvailablility.Add(PublishableContactInformationType.Availability, ContactAvailability.DoNotDisturb);
            }
            else
            {
                publishableAvailablility.Add(PublishableContactInformationType.Availability, ContactAvailability.Free);
            }
            _LyncClient.Self.BeginPublishContactInformation(
                publishableAvailablility,
                (ar) => 
                {
                    try
                    {
                    _LyncClient.Self.EndPublishContactInformation(ar);
                    }
                    catch (LyncClientException lce)
                    {
                        MessageBox.Show("Exception on publish availablility " + lce.Message);
                    }
                }
                ,null);
            SetBusy_Button.Text = "Clear meeting status";
        }

        private void Alerts_Button_Click(object sender, EventArgs e)
        {
            Alerts alertsForm = new Alerts();
            alertsForm.ShowDialog();
        }

    }
}
```

## Next steps

  - [How to: Attach a file to the content stage of a conversation](how-to-attach-a-file-to-the-content-stage-of-a-conversation.md)

  - [How to: Attach a file to the content stage of a conversation](how-to-attach-a-file-to-the-content-stage-of-a-conversation.md)

## See also

  - [What you can do with content sharing](what-you-can-do-with-content-sharing.md)

