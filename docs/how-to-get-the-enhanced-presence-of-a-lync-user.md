---
title: 'How to: Get the enhanced presence of a Lync user'
TOCTitle: 'How to: Get the enhanced presence of a Lync user'
ms:assetid: 795a04e4-89b0-4c6b-8844-3cb7267bb631
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933083(v=office.15)
ms:contentKeyID: 50877211
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Get the enhanced presence of a Lync user

Learn how to use Microsoft Lync 2013 SDK to get and display the enhanced presence that is published by a Microsoft Lync 2013 user.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Contact information and settings<br />
Prerequisites<br />
Get and display enhanced presence<br />
Display a Lync 2013 contact photo<br />
Display a Lync 2013 telephone number<br />
Code examples: Get and show enhanced presence<br />
Additional resources</p></td>
<td><p><img src="images/JJ937288.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-use-the-lync-47ded7b4">Use the Lync 2013 Model API to retrieve and publish presence</a></p></td>
</tr>
</tbody>
</table>


## Contact information and settings

A [Contact](contact-class-microsoft-lync-model_2.md) exposes two types of property collections:

  - **Contact Information**: Read only. Contact information types are published by a local user for all other users to access according to established privacy relationships. Because of privacy relationship restrictions, a local user might not be able to access a contact information value published by a remote contact. When this happens, a call into [GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) returns a null value when type requested is not available. For more information about privacy relationships, see [How to: Administer privacy relationships between Lync users](how-to-administer-privacy-relationships-between-lync-users.md).

  - **Contact Settings**: Read/Write. The setting choices for a contact are made by the local user and affect interaction with other users individually. For example, the local user John has added Mark to his contact list. John chooses the access level setting of "Workgroup" for the Mark’s contact instance. With this choice, John has given Mark access to his published contact information where appropriate for a member of John’s workgroup. Susan has also added Mark to her contact list but because Susan is in a different workgroup, she chose the access level setting of "Colleague" for Mark’s contact instance. Mark can now see Susan’s published contact information where appropriate for a member of the same enterprise.

## Prerequisites

The prerequisites for getting enhanced presence information published by a Lync user are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

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
<td><p><a href="enhanced-presence-content-in-lync-sdk.md">Enhanced presence content in Lync SDK</a></p></td>
<td><p>Introduces the concept of enhanced presence.</p></td>
</tr>
<tr class="even">
<td><p><a href="presence-publication-and-subscription-in-lync-sdk.md">Presence publication and subscription in Lync SDK</a></p></td>
<td><p>Describes the concept of contact presence publication and subscription in Microsoft Lync 2013 SDK.</p></td>
</tr>
</tbody>
</table>


## Get and display enhanced presence

All elements of enhanced presence are obtained by getting a Lync user’s [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) object and calling either one of the two overloads of the **GetContactInformation** method on the contact. You can get enhanced presence elements individually by using the [Contact.GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) method overload or a collection of elements by calling the [Contact.GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) method overload. Figure 1 shows a Windows form that displays elements of enhanced presence obtained by these methods.

**Figure 1. Windows Form with enhance presence**

![A custom contact card with phones and availability](images/JJ933083.LyncClientSDK_ContactCard(Office.15).jpg "A custom contact card with phones and availability")

The following procedure shows how to get an individual enhanced presence element. Most of these elements are string values. The picture element and telephone number element return values are treated differently and are discussed individually.

### To get an enhanced presence element

1.  Get the [LyncClient](lyncclient-class-microsoft-lync-model_2.md) instance.

2.  Read the [Client.State](client-state-property-microsoft-lync-model_2.md) property to verify that the client is signed in.
    
    For information about signing in to Microsoft Lync 2013, see [How to: Sign in to and out of Lync](https://msdn.microsoft.com/en-us/library/jj937241\(v=office.15\)).

3.  Get a **Contact** instance.
    
    For information about searching for a contact or distribution group, see [How to: Search for a contact, distribution group, or chat room](https://msdn.microsoft.com/en-us/library/jj933159\(v=office.15\)).

4.  Call the [GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) method on the **Contact** instance.

5.  Pass an enumerator of the [ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md) enumeration to specify the element of enhanced presence to return.

6.  Display the returned value if the return type is **String**.

The following table lists the [Microsoft.Lync.Model.ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md) enumerators used to provide values for figure 1.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Enumerator</p></th>
<th><p>Enhanced presence element</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.DisplayName</strong></p></td>
<td><p>Contact display name.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.Availability</strong></p></td>
<td><p>Current availability of the contact.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.Activity</strong></p></td>
<td><p>Current activity of the contact.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.OutOfficeNote</strong></p></td>
<td><p>Out of office note set by the user.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contact-uri-property-microsoft-lync-model_2.md">Uri</a></p></td>
<td><p>This is a property that is read directly from the <strong>Contact</strong> object. It is the SIP URI of the contact.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.Photo</strong></p></td>
<td><p>User photo shown in the Lync 2013 client. For information about displaying the photo, see Display a Lync 2013 contact photo.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.Company</strong></p></td>
<td><p>User employer name.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.Department</strong></p></td>
<td><p>User department name.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.PrimaryEmailAddress</strong></p></td>
<td><p>User’s primary email address.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a><strong>.ContactEndpoints</strong></p></td>
<td><p>The contact telephone numbers published by the user. For information about displaying individual telephone numbers, see Display a Lync 2013 telephone number.</p></td>
</tr>
</tbody>
</table>


## Display a Lync 2013 contact photo

The contact photo is returned from the [Contact.GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) method as a **Stream** object. The following procedures show how to display the picture in a Windows form and in a WPF window.

### To display a Lync 2013 contact photo in a Windows form

1.  On the contact whose photo is needed, call the [Contact.GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) method.

2.  Cast the returned value to a **System.IO.Stream** object.

3.  Create a new **System.Drawing.Bitmap** object by calling its constructor with the **Stream** as the argument.

4.  Set the **Image** property of a **PictureBox** control to the bitmap.
    
    The following example shows how to complete the steps in this procedure.
    
    ``` csharp
    using (Stream photoStream =
                        _Contact.GetContactInformation(ContactInformationType.Photo) as Stream)
    {
        if (photoStream != null)
        {
            Bitmap bm = new Bitmap(photoStream);
            pictureBox1.Image = bm;
        }
    }
    ```

### To display a Lync 2013 contact photo in a WPF window

1.  On the contact whose photo is needed, call the [Contact.GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) method.

2.  Cast the returned value to a **System.IO.Stream** object.

3.  Create a new **BitmapImage** object.

4.  Initialize the **BitmapImage** object

5.  Set the **StreamSource** property of the **BitmapImage** object to the stream obtained in the second step.

6.  Set the **Source** property of the **Image** object to the **BitmapImage** object.
    
    The following example sets the **Source** property of an **Image** object to a new **BitMapImage**.
    
    ``` csharp
    using (Stream photoStream =
                        _Contact.GetContactInformation(ContactInformationType.Photo) as Stream)
    {
        if (photoStream != null)
        {
            System.Windows.Media.Imaging.BitmapImage bm = new BitmapImage();
            bm.BeginInit();
            bm.StreamSource = photoStream;
            bm.EndInit();
            photoImage.Source = bm;
        }
    }
    ```

## Display a Lync 2013 telephone number

### To get and display a telephone number

1.  On the contact whose telephone numbers are needed, call the [Contact.GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) method.

2.  Cast the returned property value to **List\<object\>**.
    
    The following example gets a contact’s telephone number collection and casts the returned value to a list of objects.
    
    ``` csharp
    List<object> _endpoints = (List<object>)_Contact.GetContactInformation(ContactInformationType.ContactEndpoints);
    ```

3.  Iterate on the object list and cast individual objects to [Microsoft.Lync.Model.ContactEndpoint](contactendpoint-class-microsoft-lync-model_2.md) to get the [ContactEndpoint.Type](contactendpoint-type-property-microsoft-lync-model_2.md) property.
    
    The following example iterates on the object list and breaks when the work telephone is found.
    
    ``` csharp
    string returnValue = string.Empty;
    foreach (object endpoint in _endpoints)
    {
        ContactEndpoint phone = (ContactEndpoint)endpoint;
        if (phone.Type == ContactEndpointType.WorkPhone)
        {
            returnValue = phone.Uri;
            break;
        }
    }
    ```

## Code examples: Get and show enhanced presence

The following example declares the Windows form shown in the Get and display enhanced presence section.

``` csharp
namespace SimpleContactList
{
    partial class ContactCard
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
            this.WorkPhone_Label = new System.Windows.Forms.Label();
            this.HomePhone_Label = new System.Windows.Forms.Label();
            this.MobilePhone_Label = new System.Windows.Forms.Label();
            this.DisplayName_Label = new System.Windows.Forms.Label();
            this.ActivityString_Label = new System.Windows.Forms.Label();
            this.Availability_Label = new System.Windows.Forms.Label();
            this.Note_Label = new System.Windows.Forms.Label();
            this.URI_Label = new System.Windows.Forms.Label();
            this.flowLayoutPanel1 = new System.Windows.Forms.FlowLayoutPanel();
            this.flowLayoutPanel3 = new System.Windows.Forms.FlowLayoutPanel();
            this.OtherPhone_Label = new System.Windows.Forms.Label();
            this.button1 = new System.Windows.Forms.Button();
            this.flowLayoutPanel2 = new System.Windows.Forms.FlowLayoutPanel();
            this.pictureBox1 = new System.Windows.Forms.PictureBox();
            this.Icon_PictureBox = new System.Windows.Forms.PictureBox();
            this.Company_Label = new System.Windows.Forms.Label();
            this.Department_Label = new System.Windows.Forms.Label();
            this.PrimaryEmail_Label = new System.Windows.Forms.Label();
            this.flowLayoutPanel1.SuspendLayout();
            this.flowLayoutPanel3.SuspendLayout();
            this.flowLayoutPanel2.SuspendLayout();
            ((System.ComponentModel.ISupportInitialize)(this.pictureBox1)).BeginInit();
            ((System.ComponentModel.ISupportInitialize)(this.Icon_PictureBox)).BeginInit();
            this.SuspendLayout();
            // 
            // WorkPhone_Label
            // 
            this.WorkPhone_Label.AutoSize = true;
            this.WorkPhone_Label.Location = new System.Drawing.Point(7, 14);
            this.WorkPhone_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.WorkPhone_Label.Name = "WorkPhone_Label";
            this.WorkPhone_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.WorkPhone_Label.Size = new System.Drawing.Size(79, 29);
            this.WorkPhone_Label.TabIndex = 4;
            this.WorkPhone_Label.Text = "Work Phone";
            // 
            // HomePhone_Label
            // 
            this.HomePhone_Label.AutoSize = true;
            this.HomePhone_Label.Location = new System.Drawing.Point(7, 57);
            this.HomePhone_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.HomePhone_Label.Name = "HomePhone_Label";
            this.HomePhone_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.HomePhone_Label.Size = new System.Drawing.Size(84, 29);
            this.HomePhone_Label.TabIndex = 5;
            this.HomePhone_Label.Text = "Home Phone";
            // 
            // MobilePhone_Label
            // 
            this.MobilePhone_Label.AutoSize = true;
            this.MobilePhone_Label.Location = new System.Drawing.Point(7, 100);
            this.MobilePhone_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.MobilePhone_Label.Name = "MobilePhone_Label";
            this.MobilePhone_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.MobilePhone_Label.Size = new System.Drawing.Size(88, 29);
            this.MobilePhone_Label.TabIndex = 6;
            this.MobilePhone_Label.Text = "Mobile Phone";
            // 
            // DisplayName_Label
            // 
            this.DisplayName_Label.AutoSize = true;
            this.DisplayName_Label.Location = new System.Drawing.Point(7, 14);
            this.DisplayName_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.DisplayName_Label.Name = "DisplayName_Label";
            this.DisplayName_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.DisplayName_Label.Size = new System.Drawing.Size(85, 29);
            this.DisplayName_Label.TabIndex = 10;
            this.DisplayName_Label.Text = "Display name";
            // 
            // ActivityString_Label
            // 
            this.ActivityString_Label.AutoSize = true;
            this.ActivityString_Label.Location = new System.Drawing.Point(7, 100);
            this.ActivityString_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.ActivityString_Label.Name = "ActivityString_Label";
            this.ActivityString_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.ActivityString_Label.Size = new System.Drawing.Size(54, 29);
            this.ActivityString_Label.TabIndex = 11;
            this.ActivityString_Label.Text = "Activity";
            // 
            // Availability_Label
            // 
            this.Availability_Label.AutoSize = true;
            this.Availability_Label.Location = new System.Drawing.Point(7, 57);
            this.Availability_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.Availability_Label.Name = "Availability_Label";
            this.Availability_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.Availability_Label.Size = new System.Drawing.Size(72, 29);
            this.Availability_Label.TabIndex = 12;
            this.Availability_Label.Text = "Availability";
            // 
            // Note_Label
            // 
            this.Note_Label.AutoSize = true;
            this.Note_Label.Location = new System.Drawing.Point(7, 143);
            this.Note_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.Note_Label.Name = "Note_Label";
            this.Note_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.Note_Label.Size = new System.Drawing.Size(40, 29);
            this.Note_Label.TabIndex = 13;
            this.Note_Label.Text = "Note";
            // 
            // URI_Label
            // 
            this.URI_Label.AutoSize = true;
            this.URI_Label.Location = new System.Drawing.Point(7, 186);
            this.URI_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.URI_Label.Name = "URI_Label";
            this.URI_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.URI_Label.Size = new System.Drawing.Size(32, 29);
            this.URI_Label.TabIndex = 14;
            this.URI_Label.Text = "URI";
            // 
            // flowLayoutPanel1
            // 
            this.flowLayoutPanel1.BackColor = System.Drawing.Color.DarkGreen;
            this.flowLayoutPanel1.Controls.Add(this.DisplayName_Label);
            this.flowLayoutPanel1.Controls.Add(this.Availability_Label);
            this.flowLayoutPanel1.Controls.Add(this.ActivityString_Label);
            this.flowLayoutPanel1.Controls.Add(this.Note_Label);
            this.flowLayoutPanel1.Controls.Add(this.URI_Label);
            this.flowLayoutPanel1.FlowDirection = System.Windows.Forms.FlowDirection.TopDown;
            this.flowLayoutPanel1.Font = new System.Drawing.Font("Segoe UI", 8.074766F, System.Drawing.FontStyle.Regular, System.Drawing.GraphicsUnit.Point, ((byte)(0)));
            this.flowLayoutPanel1.ForeColor = System.Drawing.SystemColors.ButtonFace;
            this.flowLayoutPanel1.Location = new System.Drawing.Point(16, 17);
            this.flowLayoutPanel1.Margin = new System.Windows.Forms.Padding(7);
            this.flowLayoutPanel1.Name = "flowLayoutPanel1";
            this.flowLayoutPanel1.Padding = new System.Windows.Forms.Padding(7);
            this.flowLayoutPanel1.Size = new System.Drawing.Size(233, 286);
            this.flowLayoutPanel1.TabIndex = 15;
            // 
            // flowLayoutPanel3
            // 
            this.flowLayoutPanel3.BackColor = System.Drawing.Color.Navy;
            this.flowLayoutPanel3.Controls.Add(this.WorkPhone_Label);
            this.flowLayoutPanel3.Controls.Add(this.HomePhone_Label);
            this.flowLayoutPanel3.Controls.Add(this.MobilePhone_Label);
            this.flowLayoutPanel3.Controls.Add(this.OtherPhone_Label);
            this.flowLayoutPanel3.FlowDirection = System.Windows.Forms.FlowDirection.TopDown;
            this.flowLayoutPanel3.ForeColor = System.Drawing.SystemColors.ButtonHighlight;
            this.flowLayoutPanel3.Location = new System.Drawing.Point(507, 16);
            this.flowLayoutPanel3.Margin = new System.Windows.Forms.Padding(7);
            this.flowLayoutPanel3.Name = "flowLayoutPanel3";
            this.flowLayoutPanel3.Padding = new System.Windows.Forms.Padding(7);
            this.flowLayoutPanel3.Size = new System.Drawing.Size(260, 286);
            this.flowLayoutPanel3.TabIndex = 17;
            // 
            // OtherPhone_Label
            // 
            this.OtherPhone_Label.AutoSize = true;
            this.OtherPhone_Label.Location = new System.Drawing.Point(7, 143);
            this.OtherPhone_Label.Margin = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.OtherPhone_Label.Name = "OtherPhone_Label";
            this.OtherPhone_Label.Padding = new System.Windows.Forms.Padding(0, 7, 7, 7);
            this.OtherPhone_Label.Size = new System.Drawing.Size(81, 29);
            this.OtherPhone_Label.TabIndex = 8;
            this.OtherPhone_Label.Text = "Other phone";
            // 
            // button1
            // 
            this.button1.Location = new System.Drawing.Point(708, 313);
            this.button1.Name = "button1";
            this.button1.Size = new System.Drawing.Size(75, 23);
            this.button1.TabIndex = 18;
            this.button1.Text = "Close";
            this.button1.UseVisualStyleBackColor = true;
            this.button1.Click += new System.EventHandler(this.button1_Click);
            // 
            // flowLayoutPanel2
            // 
            this.flowLayoutPanel2.BackColor = System.Drawing.Color.Teal;
            this.flowLayoutPanel2.Controls.Add(this.pictureBox1);
            this.flowLayoutPanel2.Controls.Add(this.Icon_PictureBox);
            this.flowLayoutPanel2.Controls.Add(this.Company_Label);
            this.flowLayoutPanel2.Controls.Add(this.Department_Label);
            this.flowLayoutPanel2.Controls.Add(this.PrimaryEmail_Label);
            this.flowLayoutPanel2.FlowDirection = System.Windows.Forms.FlowDirection.TopDown;
            this.flowLayoutPanel2.ForeColor = System.Drawing.SystemColors.ButtonHighlight;
            this.flowLayoutPanel2.Location = new System.Drawing.Point(259, 17);
            this.flowLayoutPanel2.Name = "flowLayoutPanel2";
            this.flowLayoutPanel2.Size = new System.Drawing.Size(238, 286);
            this.flowLayoutPanel2.TabIndex = 19;
            // 
            // pictureBox1
            // 
            this.pictureBox1.Location = new System.Drawing.Point(3, 3);
            this.pictureBox1.Name = "pictureBox1";
            this.pictureBox1.Size = new System.Drawing.Size(120, 126);
            this.pictureBox1.TabIndex = 0;
            this.pictureBox1.TabStop = false;
            // 
            // Icon_PictureBox
            // 
            this.Icon_PictureBox.Location = new System.Drawing.Point(3, 135);
            this.Icon_PictureBox.Name = "Icon_PictureBox";
            this.Icon_PictureBox.Size = new System.Drawing.Size(34, 37);
            this.Icon_PictureBox.TabIndex = 1;
            this.Icon_PictureBox.TabStop = false;
            // 
            // Company_Label
            // 
            this.Company_Label.AutoSize = true;
            this.Company_Label.Location = new System.Drawing.Point(3, 175);
            this.Company_Label.Name = "Company_Label";
            this.Company_Label.Size = new System.Drawing.Size(59, 15);
            this.Company_Label.TabIndex = 2;
            this.Company_Label.Text = "Company";
            // 
            // Department_Label
            // 
            this.Department_Label.AutoSize = true;
            this.Department_Label.Location = new System.Drawing.Point(3, 190);
            this.Department_Label.Name = "Department_Label";
            this.Department_Label.Size = new System.Drawing.Size(70, 15);
            this.Department_Label.TabIndex = 3;
            this.Department_Label.Text = "Department";
            // 
            // PrimaryEmail_Label
            // 
            this.PrimaryEmail_Label.AutoSize = true;
            this.PrimaryEmail_Label.Location = new System.Drawing.Point(3, 205);
            this.PrimaryEmail_Label.Name = "PrimaryEmail_Label";
            this.PrimaryEmail_Label.Size = new System.Drawing.Size(80, 15);
            this.PrimaryEmail_Label.TabIndex = 4;
            this.PrimaryEmail_Label.Text = "Primary Email";
            // 
            // ContactCard
            // 
            this.AutoScaleDimensions = new System.Drawing.SizeF(7F, 15F);
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
            this.ClientSize = new System.Drawing.Size(793, 343);
            this.Controls.Add(this.flowLayoutPanel2);
            this.Controls.Add(this.button1);
            this.Controls.Add(this.flowLayoutPanel1);
            this.Controls.Add(this.flowLayoutPanel3);
            this.Font = new System.Drawing.Font("Segoe UI", 8.074766F, System.Drawing.FontStyle.Regular, System.Drawing.GraphicsUnit.Point, ((byte)(0)));
            this.Name = "ContactCard";
            this.Text = "Contact Card";
            this.Load += new System.EventHandler(this.ContactCard_Load);
            this.flowLayoutPanel1.ResumeLayout(false);
            this.flowLayoutPanel1.PerformLayout();
            this.flowLayoutPanel3.ResumeLayout(false);
            this.flowLayoutPanel3.PerformLayout();
            this.flowLayoutPanel2.ResumeLayout(false);
            this.flowLayoutPanel2.PerformLayout();
            ((System.ComponentModel.ISupportInitialize)(this.pictureBox1)).EndInit();
            ((System.ComponentModel.ISupportInitialize)(this.Icon_PictureBox)).EndInit();
            this.ResumeLayout(false);

        }

        #endregion

        private System.Windows.Forms.Label WorkPhone_Label;
        private System.Windows.Forms.Label HomePhone_Label;
        private System.Windows.Forms.Label MobilePhone_Label;
        private System.Windows.Forms.Label DisplayName_Label;
        private System.Windows.Forms.Label ActivityString_Label;
        private System.Windows.Forms.Label Availability_Label;
        private System.Windows.Forms.Label Note_Label;
        private System.Windows.Forms.Label URI_Label;
        private System.Windows.Forms.FlowLayoutPanel flowLayoutPanel1;
        private System.Windows.Forms.FlowLayoutPanel flowLayoutPanel3;
        private System.Windows.Forms.Label OtherPhone_Label;
        private System.Windows.Forms.Button button1;
        private System.Windows.Forms.FlowLayoutPanel flowLayoutPanel2;
        private System.Windows.Forms.PictureBox pictureBox1;
        private System.Windows.Forms.PictureBox Icon_PictureBox;
        private System.Windows.Forms.Label Company_Label;
        private System.Windows.Forms.Label Department_Label;
        private System.Windows.Forms.Label PrimaryEmail_Label;
    }
}
```

The following example sets the values displayed on the previous form.

``` csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using System.IO;
using System.Diagnostics;

namespace SimpleContactList
{
    public partial class ContactCard : Form
    {
        ContactModel _ContactModel;
        LyncClient _LyncClient;
        public ContactCard()
        {
            InitializeComponent();
        }
        public ContactCard(ContactModel contact)
        {
            InitializeComponent();
            _LyncClient = LyncClient.GetClient();
            _ContactModel = contact;
            _ContactModel.ContactInformationUpdated += new EventHandler<ContactPresenceChangedEventArgs>(_ContactModel_ContactInformationUpdated);
        }

        void _ContactModel_ContactInformationUpdated(object sender, ContactPresenceChangedEventArgs e)
        {
            GetContactCardInformation();
        }

        private void ContactCard_Load(object sender, EventArgs e)
        {
            GetContactCardInformation();
        }

        private void GetContactCardInformation()
        {
            WorkPhone_Label.Text = "Work: " + _ContactModel.WorkPhone;
            HomePhone_Label.Text = "Home: " + _ContactModel.HomePhone;
            MobilePhone_Label.Text = "Mobile: " + _ContactModel.MobilePhone;
            OtherPhone_Label.Text = "Other: " + _ContactModel.OtherPhone;
            URI_Label.Text = "URI: " + _ContactModel.Uri;
            Note_Label.Text = "Note: " + System.Environment.NewLine + _ContactModel.ContactNote;
            Availability_Label.Text = "Availability: " + _ContactModel.Availability;
            ActivityString_Label.Text = "Activity: " + _ContactModel.ActivityString;
            DisplayName_Label.Text = "Name: " + _ContactModel.DisplayName;
            Company_Label.Text = "Company: " _ContactModel.CompanyName;
            Department_Label.Text = "Department: " + _ContactModel.DepartmentName;
            PrimaryEmail_Label.Text = "Email: " + _ContactModel.PrimaryEmail;
            SetContactImages();
        }
        private void button1_Click(object sender, EventArgs e)
        {
            this.Close();
        }

        /// <summary>
        /// Gets the contact's photo from Lync and updates the corresponding element in the user interface
        /// </summary>
        private void SetContactImages()
        {
            try
            {
                using (Stream photoStream =
                     _ContactModel.LyncContact.GetContactInformation(ContactInformationType.Photo) as Stream)
                {
                    if (photoStream != null)
                    {
                        Bitmap bm = new Bitmap(photoStream);
                        pictureBox1.Image = bm;
                    }
                }
                using (Stream iconStream =
                     _ContactModel.IconStream)
                {
                    if (iconStream != null)
                    {
                        Bitmap iconbm = new Bitmap(iconStream);
                        Icon_PictureBox.Image = iconbm;
                    }
                }
            }
            catch (LyncClientException e)
            {
                Debug.WriteLine(e);
            }
        }

    }
}
```

The following example encapsulates a [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) object in a class that handles events on the **Contact** and exposes enhanced information as a set of public properties.

``` csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Text;
using System.Runtime.InteropServices;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;
using WinForm = System.Windows.Forms;
using System.Diagnostics;
using System.IO;

namespace SimpleContactList
{
    public delegate void ContactPropertyChangedDelegate(ContactModel source, ContactSettingChangedEventArgs data);
    public delegate void ContactUriPropertyChangedDelegate(string OldUri, string NewUri);

    public class ContactModel : IDisposable
    {
        #region private fields
        private Contact _Contact;
        private string _ContactCardInformation = string.Empty;
        private Boolean disposed = false;
        private Dictionary<ContactInformationType, object> _ContactInformation = new Dictionary<ContactInformationType, object>();
        List<object> _endpoints;
        LyncClient _LyncClient;

        #endregion

        #region pubic events

        //ContactManagerModel registers for this event to listen for changes in presence items
        //event generic type is declared in  UCInterfaces.EventArgs
        public event EventHandler<ContactPresenceChangedEventArgs> ContactInformationUpdated;
        public event ContactUriPropertyChangedDelegate ContactUriChangedEvent;

        //ContactManagerModel registers for this event to listen for a contactModel property change
        public event ContactPropertyChangedDelegate ContactSettingChangedEvent;

        #endregion

        #region public properties

        /// <summary>
        /// Returns inner Lync Client Contact instance modelled by this.
        /// </summary>
        public Contact LyncContact
        {
            get
            {
                return _Contact;
            }
        }

        /// <summary>
        /// Returns the current activity of the Contact.
        /// </summary>
        public string ActivityString
        {
            get
            {
                object activityString = _Contact.GetContactInformation(ContactInformationType.Activity);
                return activityString.ToString();
            }
        }

        /// <summary>
        /// Returns the current activity of the Contact.
        /// </summary>
        public string Availability
        {
            get
            {
                ContactAvailability currentAvailability = (ContactAvailability)_Contact.GetContactInformation(ContactInformationType.Availability);
                return currentAvailability.ToString();
            }
        }

        /// <summary>
        /// Returns a list of groups to which this contact belongs.
        /// </summary>
        public List<string> ContactCustomGroups
        {
            get
            {
                List<string> returnValue = new List<string>();
                try
                {
                    if (_Contact.CustomGroups != null && _Contact.CustomGroups.Count > 0)
                    {
                        foreach (Group g in _Contact.CustomGroups)
                        {
                            returnValue.Add(g.Name);
                        }
                    }
                }
                catch (COMException) { }
                return returnValue;
            }
        }

        /// <summary>
        /// Returns either the OOF note or personal note of the contact.
        /// </summary>
        public string ContactNote
        {
            get
            {
                string returnValue = string.Empty;
                string personalNote = string.Empty;
                string OOFNote = string.Empty;
                string DefaultNote = string.Empty;
                OOFNote = (string)_Contact.GetContactInformation(ContactInformationType.OutOfficeNote);
                if (OOFNote == null)
                {
                    personalNote = (string)_Contact.GetContactInformation(ContactInformationType.PersonalNote);
                    if (personalNote != null)
                    {
                        returnValue = personalNote;
                    }
                    else
                    {
                        returnValue = string.Empty;
                    }
                }
                else
                {
                    returnValue = OOFNote;
                }
                return returnValue;
            }
        }

        /// <summary>
        /// Returns the display name of the contact.
        /// </summary>
        public string DisplayName
        {
            get
            {
                try
                {
                    string contactName = string.Empty;
                    contactName = _Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                    return contactName;
                }
                catch (ItemNotFoundException ce)
                {
                    WinForm.MessageBox.Show("Lync Exception on ContactInformationType.DisplayName from contact" + ce.Message);
                    return "No Display Name";
                }
            }
        }

        /// <summary>
        /// Returns the Uri of the contact.
        /// </summary>
        public string Uri
        {
            get
            {
                string returnValue = string.Empty;
                returnValue = _Contact.Uri;
                return returnValue;
            }
        }
        public Stream PhotoStream
        {
            get
            {
                return _Contact.GetContactInformation(ContactInformationType.Photo) as Stream;
            }
        }
        public Stream IconStream
        {
            get
            {
                return _Contact.GetContactInformation(ContactInformationType.IconStream) as Stream;
            }
        }
        public string WorkPhone
        {
            get
            {
                string returnValue = string.Empty;
                foreach (object endpoint in _endpoints)
                {
                    ContactEndpoint phone = (ContactEndpoint)endpoint;
                    if (phone.Type == ContactEndpointType.WorkPhone)
                    {
                        returnValue = phone.Uri;
                        break;
                    }
                }
                return returnValue;
            }
        }
        public string HomePhone
        {
            get
            {
                string returnValue = string.Empty;
                foreach (object endpoint in _endpoints)
                {
                    ContactEndpoint phone = (ContactEndpoint)endpoint;
                    if (phone.Type == ContactEndpointType.HomePhone)
                    {
                        returnValue = phone.Uri;
                        break;
                    }
                }
                return returnValue;
            }
        }
        public string MobilePhone
        {
            get
            {
                string returnValue = string.Empty;
                foreach (object endpoint in _endpoints)
                {
                    ContactEndpoint phone = (ContactEndpoint)endpoint;
                    if (phone.Type == ContactEndpointType.MobilePhone)
                    {
                        returnValue = phone.Uri;
                        break;
                    }
                }
                return returnValue;
            }
        }
        public string VoiceMail
        {
            get
            {
                string returnValue = string.Empty;
                foreach (object endpoint in _endpoints)
                {
                    ContactEndpoint phone = (ContactEndpoint)endpoint;
                    if (phone.Type == ContactEndpointType.VoiceMail)
                    {
                        returnValue = phone.Uri;
                        break;
                    }
                }
                return returnValue;
            }
        }
        public string OtherPhone
        {
            get
            {
                string returnValue = string.Empty;
                foreach (object endpoint in _endpoints)
                {
                    ContactEndpoint phone = (ContactEndpoint)endpoint;
                    if (phone.Type == ContactEndpointType.OtherPhone)
                    {
                        returnValue = phone.Uri;
                        break;
                    }
                }
                return returnValue;
            }
        }

        public string CompanyName
        {
            get
            {
                return _Contact.GetContactInformation(ContactInformationType.Company).ToString();
            }
        }
        public string DepartmentName
        {
            get
            {
                return _Contact.GetContactInformation(ContactInformationType.Department).ToString();
            }
        }
        public string PrimaryEmail
        {
            get
            {
                return _Contact.GetContactInformation(ContactInformationType.PrimaryEmailAddress).ToString();
            }
        }

        #endregion

        #region public methods

        /// <summary>
        /// Overrides the ToString() method allowing an instance of ContactModel to be added to a UI element that
        /// calls ToString() on this object.
        /// </summary>
        /// <returns>string. A set of contact information items.</returns>
        public override string ToString()
        {
            string returnValue = string.Empty;
            string activityDescription = null;
            List<object> collaborationPhones = null;

            activityDescription = (string)_Contact.GetContactInformation(ContactInformationType.Activity);
            collaborationPhones = (List<object>)_Contact.GetContactInformation(ContactInformationType.ContactEndpoints);

            if (collaborationPhones != null)
            {
                returnValue += activityDescription;
                returnValue += "\r\nPhones:";
                foreach (object phone in collaborationPhones)
                {
                    ContactEndpoint anEndpoint = (ContactEndpoint)phone;
                    returnValue += "\r\nType: "
                        + anEndpoint.Type.ToString()
                        + " DisplayName: "
                        + anEndpoint.DisplayName
                        + " Uri: "
                        + anEndpoint.Uri;

                }
            }
            returnValue += "\r\nPersonal note: " + _Contact.GetContactInformation(ContactInformationType.PersonalNote);
            returnValue += "\r\nOOF note: " + _Contact.GetContactInformation(ContactInformationType.OutOfficeNote);

            return returnValue;
        }

        public ContactAvailability LyncAvailability()
        {
            ContactAvailability returnValue = (ContactAvailability)_Contact.GetContactInformation(ContactInformationType.Availability);
            return returnValue;
        }

        #endregion

        #region private helpers

        /// <summary>
        /// returns string containing availability and/or calendar state changes
        /// </summary>
        /// <param name="source">Contact. The contactModel whose presence has changed</param>
        /// <param name="data">PresenceItemsChangedEventArgs. A collection of presence types whose values changed</param>
        /// <returns>string. String formed of changed values and type names</returns>
        private string ListChangedAvailability(Contact source, ContactInformationChangedEventArgs data)
        {
            string returnValue = string.Empty;
            StringBuilder sb = new StringBuilder();
            Boolean raiseUpdate = false;
            if (data.ChangedContactInformation.Contains(ContactInformationType.Availability))
            {
                //get actual contactModel availability (Will be int value within OCOM availaiblity ranges)
                ContactAvailability availEnum = (ContactAvailability)source.GetContactInformation(ContactInformationType.Availability);
                string activityString = (string)source.GetContactInformation(ContactInformationType.Activity);
                sb.Append(availEnum.ToString() + " " + activityString);
                raiseUpdate = true;
            }

            if (raiseUpdate)
            {
                returnValue = "Updated availability for "
                + source.GetContactInformation(ContactInformationType.DisplayName).ToString()
                + System.Environment.NewLine
                + sb.ToString();
            }

            return returnValue;
        }

        /// <summary>
        /// Merge changed presence item values dictionary with master contactModel presence item dictionary
        /// </summary>
        /// <param name="changedItems">IDictionary Changed items</param>
        private void UpdateContactCardProperties(IDictionary<ContactInformationType, object> changedItems)
        {
            //iterate on changeItems and update master dictionary with the changed value
            if (_ContactInformation == null)
            {
                _ContactInformation = new Dictionary<ContactInformationType, object>();
            }
            foreach (ContactInformationType t in changedItems.Keys)
            {
                object newValue;
                if (changedItems.Values != null)
                {
                    if (changedItems.TryGetValue(t, out newValue))
                    {
                        if (_ContactInformation.ContainsKey(t))
                        {
                            _ContactInformation.Remove(t);
                        }
                        _ContactInformation.Add(t, newValue);
                    }
                }
            }
        }
        #endregion

        #region Contact Event handlers

        /// <summary>
        /// Alerts user when a contactModel Uri has changed
        /// </summary>
        /// <param name="source">object. Contact whose Uri has changed</param>
        /// <param name="data">UriChangedEventArgs Event data</param>
        void _Contact_OnUriChanged(Object source, UriChangedEventArgs data)
        {
            if (ContactUriChangedEvent != null)
            {
                ContactUriChangedEvent(data.OldUri, data.NewUri);
            }
        }

        /// <summary>
        /// Handles event raised when contactModel presence item collection has been updated.
        /// </summary>
        /// <param name="source">object. Contact whose information has been updated.</param>
        /// <param name="data">ContactInformationChangedEventArgs. The contact information that changed.</param>
        /// <remarks>This callback is used to update the public contactModel card string class property ContactCardInformation.
        /// The event data parameter exposes a member property, ChangedPresenceItems. This property is a list of ContactInformationType. The types in 
        /// the list are the presence item types whose change resulted in this state change event.
        /// </remarks>
        void _Contact_OnInformationChanged(Object source, ContactInformationChangedEventArgs data)
        {

            try
            {
                Contact _contact = (Contact)source;
                string newCard = ListChangedAvailability(_contact, data);

                _ContactCardInformation = newCard; // presence contactModel card  values

                if (ContactInformationUpdated != null)
                {
                    Dictionary<int, object> changedValues = new Dictionary<int, object>();
                    ArrayList changedTypes = new ArrayList();

                    IDictionary<ContactInformationType, object> pd = _contact.GetContactInformation(data.ChangedContactInformation);
                    //call local contactModel card presence dictionary maintainence method here.
                    UpdateContactCardProperties(pd);

                    if (data.ChangedContactInformation.Contains(ContactInformationType.Availability))
                    {
                        changedTypes.Add(ContactInformationType.Availability);
                        changedValues.Add(changedTypes.Count, pd[ContactInformationType.Availability]);
                    }

                    //Raise application event to listeners
                    ContactInformationUpdated(this, new ContactPresenceChangedEventArgs(changedTypes, changedValues));
                }
            }
            catch (ItemAlreadyExistException ce)
            {
                WinForm.MessageBox.Show("Contact Information Exception, Contact.OnInformationChanged " + ce.Message);
            }
            catch (System.IO.InvalidDataException x)
            {
                WinForm.MessageBox.Show("Invalid Data Exception, Contact.OnInformationChanged " + x.Message);
            }
        }

        /// <summary>
        /// Handles the event raised when the state of a contactModel is changed. State change is limited to changes to the contactModel properties
        /// </summary>
        /// <param name="source">IContact Contact instance that changed</param>
        /// <param name="data">IContactPropertyChangedEventArgs attribute of contactModel state that changed</param>
        void _ContactSettingChanged(Object source, ContactSettingChangedEventArgs data)
        {
            if (ContactSettingChangedEvent != null)
            {
                ContactSettingChangedEvent(this, data);
            }
        }
        #endregion

        #region constructors
        public ContactModel(Contact pContact)
        {

            _Contact = pContact;

            try
            {
                _LyncClient = LyncClient.GetClient();
                //Create a collection of contact information types to be displayed on a contact card
                //Collection is passed into GetContactInformation and corresponding contact card values are returned.
                List<ContactInformationType> myContactCardItems = new List<ContactInformationType>();
                myContactCardItems.Add(ContactInformationType.Company);
                myContactCardItems.Add(ContactInformationType.DisplayName);
                myContactCardItems.Add(ContactInformationType.PersonalNote);

                _ContactInformation = pContact.GetContactInformation(myContactCardItems) as Dictionary<ContactInformationType, object>;
                Debug.WriteLine(_Contact.GetContactInformation(ContactInformationType.ContactEndpoints).GetType().Name);
                _endpoints = (List<object>)_Contact.GetContactInformation(ContactInformationType.ContactEndpoints);
            }
            catch (LyncClientException) { }

            //Register for events raised when a subscribed contact re-publishes interesting information.
            _Contact.SettingChanged += new EventHandler<ContactSettingChangedEventArgs>(_ContactSettingChanged);
            _Contact.ContactInformationChanged += new EventHandler<ContactInformationChangedEventArgs>(_Contact_OnInformationChanged);
            _Contact.UriChanged += new EventHandler<UriChangedEventArgs>(_Contact_OnUriChanged);

        }

        #endregion

        #region IDisposable Members

        public void Dispose()
        {
            this.Dispose(true);
            GC.SuppressFinalize(this);
        }
        private void Dispose(Boolean disposing)
        {
            if (!this.disposed)
            {
                this._Contact.SettingChanged -= _ContactSettingChanged;
                this._Contact.ContactInformationChanged -= _Contact_OnInformationChanged;
                this._Contact.UriChanged -= _Contact_OnUriChanged;
            }
            this.disposed = true;
        }

        #endregion
    }
}
```

## Additional resources

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

  - [How to: Use presence information in an application](how-to-use-presence-information-in-an-application.md)

