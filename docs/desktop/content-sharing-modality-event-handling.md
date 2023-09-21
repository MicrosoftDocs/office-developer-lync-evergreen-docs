---
title: Content sharing modality event handling
TOCTitle: Content sharing modality event handling
ms:assetid: 3250839b-e7c1-4750-b244-dfa7c839aa63
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937294(v=office.15)
ms:contentKeyID: 50877119
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
description: Master Microsoft Lync 2013 API content sharing modality with this comprehensive guide. Learn to make your UI responsive to events in Lync 2013 conversations.
---

# Content sharing modality event handling

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about making your application UI responsive to the events raised by Microsoft Lync 2013 API content sharing modality in Lync 2013 conversations.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Content sharing modality events<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Content sharing modality events

The sharing stage of a Lync 2013 conversation window allows conversation participants to queue and unqueue multiple types of sharing content in a logical entity that can be thought of as a content bin. Only one shareable content item can be shown on the sharing stage at a time. Any conversation presenter can be made the presenter of the active content or become a content presenter when they share content that they own.

The four events exposed by the [Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality](https://msdn.microsoft.com/library/jj266998\(v=office.15\)) are as follows:

  - [ContentSharingModality.ContentAdded](https://msdn.microsoft.com/library/jj293541\(v=office.15\))

  - [ContentSharingModality.ContentRemoved](https://msdn.microsoft.com/library/jj293209\(v=office.15\))

  - [ContentSharingModality.ActiveContentChanged](https://msdn.microsoft.com/library/jj278043\(v=office.15\))

  - [ContentSharingModality.ActivePresenterChanged](https://msdn.microsoft.com/library/jj266964\(v=office.15\))

In addition, the **ContentSharingModality** raises all the events that it inherits from the base [Microsoft.Lync.Model.Conversation.Modality](https://msdn.microsoft.com/library/jj274796\(v=office.15\)) class.

### ContentAdded event

A presenter has added a new shareable content item to the content bin. The [ContentSharingModality.ContentAdded](https://msdn.microsoft.com/library/jj293541\(v=office.15\)) event should be used to update your client UI with the title of a new content bin item. The event data state object provides a reference to the new [ShareableContent](https://msdn.microsoft.com/library/jj277217\(v=office.15\)) object. You should register for events on the **ShareableContent** object when it's added to the content bin.

The following example adds the title of the new content to a list in the UI and then enables a command button.

```csharp
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

            //Invoke a delegate that updates a property on a UI control by adding the
            //title of the newly added content to a list box.
            this.Invoke(ListAdder, new object[] { Content_Listbox, newItem });

            //Invoke a delegate that enables the Share button on the UI
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton)
                , new object[] { ContentShare_Button, true });
        }
```

### ContentRemoved event

A presenter has removed a shareable content item from the content bin. The [ContentSharingModality.ContentRemoved](https://msdn.microsoft.com/library/jj293209\(v=office.15\)) event is used to update your client UI to remove the title of the removed content from a content bin list and to unregister for content sharing events on the removed content.

The following example refreshes a UI list of content bin items.

``` 
        /// <summary>
        /// Raised when an item is removed from the content bin
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ContentRemoved(object sender, ContentCollectionChangedEventArgs e)
        {
            //Invokes a delegate that clears and re-loads a UI list of items in the content bin.
            this.Invoke(new ClearAllListItemsDelegate(ClearAllListItems), new object[] { Content_Listbox});
            foreach (ShareableContent sc in ((ContentSharingModality)_conversation.Modalities[ModalityTypes.ContentSharing]).ContentCollection)
            {
                string newItem = sc.Type.ToString() + "-" + sc.Title;
                this.Invoke(new AddAListItemDelegate(AddAListItem), new object[] { Content_Listbox, newItem });
            }
        }
```

### ActiveContentChanged event

A presenter has swapped one content bin sharing item for another item. The [ContentSharingModality.ActiveContentChanged](https://msdn.microsoft.com/library/jj278043\(v=office.15\)) event tells you that a conversation participant has swapped one content bin item for a different one on the sharing stage. An application UI should show the current active content presenter and command buttons for actions that can be taken on active content. Use this event to get the new active content presenter and enable command buttons that are appropriate for the type of content that is being presented.

The following example gets the title of the newly shared content and then enables or disables the command buttons that are appropriate for the content type.

```csharp
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
                EnableDisableButtonDelegate ButtonDisableDelegate = new EnableDisableButtonDelegate(EnableDisableButton);
                if (e.ActiveContent.Type == ShareableContentType.PowerPoint)
                {
                    this.Invoke(ButtonDisableDelegate, new object[] { GoBack_Button, true });
                    this.Invoke(ButtonDisableDelegate, new object[] { GoForward_Button, true });
                    this.Invoke(ButtonDisableDelegate, new object[] { ClearAnnotations_Button, false });
                    Int32 hrReason;
                    if (e.ActiveContent.CanInvoke(ShareableContentAction.ClearAllAnnotations, out hrReason))
                    {
                        this.Invoke(ButtonDisableDelegate, new object[] { ClearAnnotations_Button, true });
                    }

                }
                else if (e.ActiveContent.Type == ShareableContentType.Whiteboard)
                {
                    Int32 hrReason;
                    if (e.ActiveContent.CanInvoke(ShareableContentAction.ClearAllAnnotations, out hrReason))
                    {
                        this.Invoke(ButtonDisableDelegate, new object[] { ClearAnnotations_Button, true });
                    }
                    if (e.ActiveContent.CanInvoke(ShareableContentAction.SaveAnnotation, out hrReason))
                    {
                        this.Invoke(ButtonDisableDelegate, new object[] { SaveAnnotations_Button, true });
                    }

                    this.Invoke(ButtonDisableDelegate, new object[] { GoBack_Button, false });
                    this.Invoke(ButtonDisableDelegate, new object[] { GoForward_Button, false });
                }
            }
        }
```

### ActivePresenterChanged event

The presenter of the current active shareable content has changed or the active content has been swapped with content owned by a different presenter.

The following example updates a label in the application UI with the name of the current presenter.

```csharp
        /// <summary>
        /// Raised when the active presenter in the conversation changes
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ContentSharing_Form_ActivePresenterChanged(object sender, ActivePresenterChangedEventArgs e)
        {
            if (e.ActivePresenter != null)
            {
                this.Invoke(
                    new ChangeLabelTextDelegate(ChangeLabelText),
                    new object[] {Presenter_Label, 
                    e.ActivePresenter.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString()});
            }
        }
```

## See also

  - [Beyond the basics: Content sharing](beyond-the-basics-content-sharing.md)

