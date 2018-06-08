---
title: Shareable content event handling
TOCTitle: Shareable content event handling
ms:assetid: cbe90800-5c33-4b51-a9cb-9fde695411c7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933192(v=office.15)
ms:contentKeyID: 50877334
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Shareable content event handling

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about making your Microsoft Lync 2013 SDK-enabled application UI more responsive by handling events raised on the [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/en-us/library/jj277217\(v=office.15\)) class.

**Last modified:** January 07, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
ShareableContent events<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## ShareableContent events

A shared content bin item allows your application to perform any of six different operations on it, depending on the state of the item. In addition, properties of a shared content item can change during a conversation and a properly designed application UI should be responsive to such property changes.

The three events exposed by the [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/en-us/library/jj277217\(v=office.15\)) class are as follows:

  - [ShareableContent.ActionAvailabilityChanged](https://msdn.microsoft.com/en-us/library/jj267657\(v=office.15\))

  - [ShareableContent.PropertyChanged](https://msdn.microsoft.com/en-us/library/jj266446\(v=office.15\))

  - [ShareableContent.StateChanged](https://msdn.microsoft.com/en-us/library/jj276344\(v=office.15\))

### ActionAvailabilityChanged event

The actions that you can perform on a shareable content item include:

  - Saving annotations that participants have added to the shared content item.

  - Clearing all annotations from a shared content item.

  - Synchronizing with the presenter’s view of a shared PowerPoint slide deck.

  - Taking over as the presenter of the active shared content item.

  - Moving a shareable content item from the content bin to the shared stage.

  - Removing a shared content item from the sharing stage and putting it back into the content bin.

The availability of these actions depends on the current state of a shareable content item. For example, a shareable content item that is in the active state does not allow the [ShareableContent.Present](https://msdn.microsoft.com/en-us/library/jj276346\(v=office.15\)) operation because it is already being presented on the sharing stage. As the state of a shareable content object changes and actions become available or unavailable, this event is raised. Use the event handler to enable or disable command buttons on your UI. You should register for this event in the event handler for the [ContentSharingModality.ContentAdded](https://msdn.microsoft.com/en-us/library/jj293541\(v=office.15\)) event.

The following event handler enables or disables command buttons according to the current availability of an action on a **ShareableContent** object.

```csharp
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
```

### StateChanged event

A properly designed application UI should show users the current state of all items in the conversation sharing content bin. To do this, you must register for the **StateChanged** event on each shareable content item as it is added to the content bin. The registration should be done in the [ContentSharingModality.ContentAdded](https://msdn.microsoft.com/en-us/library/jj293541\(v=office.15\)) event.

The following example updates a content bin list in the UI with the current state of a shareable item.

```csharp
        /// <summary>
        /// Raised when the state of a shareable content item changes as the content is 
        /// uploaded, moved to the sharing stage or moved off of the sharing stage
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Item_StateChanged(object sender, ShareableContentStateChangedEventArgs e)
        {
            ShareableContent item = (ShareableContent)sender;
            string oldItem = item.Type.ToString() + "-" + item.Title + "-" + e.OldState.ToString();
            string newItem = item.Type.ToString() + "-" + item.Title + "-" + e.NewState.ToString();
            this.Invoke(new ChangeAListItemDelegate(ChangeAListItem), new object[] { Content_Listbox, oldItem, newItem });
        }
```

### PropertyChanged event

Several properties of a shareable content item can be changed over time, two of which can be changed by a conversation participant. The [ShareableContentProperty](https://msdn.microsoft.com/en-us/library/jj293192\(v=office.15\))**.Title** property is changed when the item owner renames the item and the [ShareableContentProperty](https://msdn.microsoft.com/en-us/library/jj293192\(v=office.15\))**.Presenter** property is changed when a different participant takes over as presenter.

The following example writes to the system console with the ID of a content bin item and the new title.

``` 
        /// <summary>
        /// Raised when a property of a ShareableContent item changes
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Item_PropertyChanged(object sender, ShareableContentPropertyChangedEventArgs e)
        {
            ShareableContent shareableContent = (ShareableContent)sender;
            if (e.Property == ShareableContentProperty.Title)
            {
                System.Diagnostics.Debug.WriteLine(
                    "The Title of the content with Id " +
                    shareableContent.Properties[ShareableContentProperty.Id].ToString() +
                    " has changed. The new title is " +
                    e.Value.ToString());
            }
        }
```

## See also

  - [Beyond the basics: Content sharing](beyond-the-basics-content-sharing.md)

