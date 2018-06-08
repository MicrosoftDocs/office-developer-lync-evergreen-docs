---
title: Putting it all together
TOCTitle: Putting it all together
ms:assetid: 587d2021-9059-4e90-ade4-0ce820947f7c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn551194(v=office.15)
ms:contentKeyID: 60829947
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Putting it all together

Now we are ready to hook up the underlying UCWA plumbing into our Windows Store app to make our application run end-to-end.


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
Parse UCWA resources in XML  
Make the application run end-to-end  
Additional resources  

## Parse UCWA resources in XML

As has been shown, programming UCWA involves traversing from one resource to another following a sequence of HTTP requests and responses. At any time, a UCWA application can only move to an available resource that is embedded in or linked to from a currently obtained resource. The steps below illustrate how to leverage the [System.Xml.Linq](http://msdn.microsoft.com/en-us/library/system.xml.linq\(v=vs.110\).aspx) name to parse the raw UCWA resources in XML.

1.  From **Solution Explorer** in Visual Studio, right click the application project name (**WinStoreUcwaAppHello**) to select the **Add-\>class** menu options.

2.  In the **Add New Item** popup window, enter "UcwaResource" as the name of the to-be-created class.

3.  In the newly created UcwaResource.cs file, add the using System.Xml.Linq and using System.IO statements to the using statement block and make the class public. The modified code file should looks like this.
    
    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    
    using System.Xml.Linq;
    using System.IO;
    
    namespace WinStoreUcwaAppHello
    {
        public class UcwaResource
        {
        }
    }
    ```

4.  Add to the UcwaResource class definition the following protected field:
    
    ```csharp
            protected XElement xElem = null;
    ```
    
    This will hold the raw XML data in the application’s cache.

5.  Add to the class definition the following class constructors:
    
    ```csharp
            #region Constructors
            public UcwaResource(Stream xmlStream)
            {
                var xDoc = XDocument.Load(xmlStream);
                if (xDoc != null)
                    xElem = xDoc.Root;
            }
            public UcwaResource(XElement xElement)
            {
                xElem = xElement;
            }
            public UcwaResource(string xmlBlock)
            {
                xElem = XElement.Parse(xmlBlock);
            }
            #endregion Constructors
    ```
    
    The constructor taking as input an XML [Stream](http://msdn.microsoft.com/en-us/library/system.io.stream\(v=vs.110\).aspx) object is useful to encapsulate the UcwaResource class from the output of an HTTP response. The constructor taking as input an [XElement](http://msdn.microsoft.com/en-us/library/system.xml.linq.xelement\(v=vs.110\).aspx) instance can be useful to instantiate the UcwaResource class to work with an embedded resource that is a child element of an encapsulated resource.

6.  Add to the UcwaResource class the following member definitions for parsing the attributes of a UCWA resource.
    
    ```csharp
            #region attributes of the resource element:
            private string GetAttributeValue(string attrName)
            {
                return xElem.Attributes(attrName).Select(a => a.Value).FirstOrDefault();
            }
            public string Name { get { return GetAttributeValue("rel"); } }
            public string Uri { get { return this.GetAttributeValue("href"); } }
            public string Xmlns { get { return this.GetAttributeValue("xmlns"); } }
            #endregion resource element's attributes
    ```

7.  Add to the UcwaResource class the following member definitions for parsing the properties of a UCWA resource.
    
    ```csharp
            #region of Properties of the resource
            public IEnumerable<XElement> Properties { get { return xElem.Elements().Where(r => r.Name.LocalName == "property"); } }
            public IEnumerable<string> PropertyNames { get { return from prop in this.Properties select prop.Attribute("name").Value; } }
            public string GetPropertyValue(string propName)
            {
                return (from prop in this.Properties where prop.Attribute("name").Value == propName select prop.Value).FirstOrDefault();
            }
            #endregion of Properties of the resource.
    ```
    
    Using the [System.Xml.Linq](http://msdn.microsoft.com/en-us/library/system.xml.linq\(v=vs.110\).aspx) namespace, XML data can be parsed through elegant and powerful SQL-like queries, without elaborate coding efforts.

8.  Add to the class definition the following member definitions for parsing the links of a UCWA resource.
    
    ```csharp
            #region Links of the resource
            public IEnumerable<XElement> Links { get { return xElem.Elements().Where(l => l.Name.LocalName == "link"); } }
            public IEnumerable<string> LinkNames { get { return from link in this.Links select link.Attribute("rel").Value; } }
            public string GetLinkUri(string linkName) { return (from link in this.Links where link.Attribute("rel").Value == linkName select link.Attribute("href").Value).FirstOrDefault(); }
            #endregion Links of the resource
    ```
    
    Here a link name is defined as the rel attribute value of the link and the link Uri as its href attribute value.

9.  Add to the class definition the following member definitions for parsing the embedded resources of a UCWA resource.
    
    ```csharp
            #region of the embedded resources
            public UcwaResource GetEmbeddedResource(string name) { return new UcwaResource(this.GetEmbeddedResourceElement(name)); }
            public IEnumerable<XElement> EmbeddedResourceElements { get { return xElem.Elements().Where(r => r.Name.LocalName == "resource"); } }
            public IEnumerable<string> EmbeddedResourceNames { get { return from res in this.EmbeddedResourceElements select res.Attribute("rel").Value; } }
            public string GetEmbeddedResourceUri(string resourceName)
            {
                var uri = GetLinkUri(resourceName);
                if (string.IsNullOrEmpty(uri))
                    uri = (from res in this.EmbeddedResourceElements where res.Attribute("rel").Value == resourceName select res.Attribute("href").Value)
                        .FirstOrDefault();
                return uri;
            }
            public XElement GetEmbeddedResourceElement(string resourceName)
            {
                return (from res in this.EmbeddedResourceElements where res.Attribute("rel").Value == resourceName select res).FirstOrDefault();
            }
            #endregion of the embedded resources
    ```
    
    Here, an embedded resource can be returned as an either UcwaResource object or an [XElement](http://msdn.microsoft.com/en-us/library/system.xml.linq.xelement\(v=vs.110\).aspx).

The class definition listed above should work with any UCWA resources. You can add customized behaviors to specific resources of your choosing.

## Make the application run end-to-end

Making the application run involves executing various parts (as discussed above) in response to user input. The steps below illustrate this process. The outcome of this example

1.  Open the MePage.xaml.cs file in the Visual Studio code editor and add a private class field to hold a UcwaApp instance.
    
    ```csharp
            UcwaApp UcwaApp;
    ```

2.  Add the this.UcwaApp = new UcwaApp() statement to the beginning of the MePage constructor. The modified constructor looks as follows.
    
    ```csharp
            public MePage()
            {
                this.UcwaApp = new UcwaApp();
    
                this.InitializeComponent();
                this.navigationHelper = new NavigationHelper(this);
                this.navigationHelper.LoadState += navigationHelper_LoadState;
                this.navigationHelper.SaveState += navigationHelper_SaveState;
            }
    ```

3.  Change the navigationHelper\_LoadState method as follows.
    
    ```csharp
            private async void navigationHelper_LoadState(object sender, LoadStateEventArgs e)
            {
                SignInParameter parameter = e.NavigationParameter as SignInParameter;
                if (!this.UcwaApp.IsSignedIn)
                {
                    if (parameter != null)
                    {
                        var statusCode = await this.UcwaApp.SignIn(parameter.UserName, parameter.Password);
                        if (statusCode != System.Net.HttpStatusCode.OK)
                            return;
                    }
                    else
                    {
                        return;
                    }
                }
    
                // Show local user info.
                textBlockMyName.Text = this.UcwaApp.Me.DisplayName +
                    ", " + this.UcwaApp.Me.Title + ", " + this.UcwaApp.Me.Department + ", " + this.UcwaApp.Me.Uri;
                textBoxNote.Text = this.UcwaApp.Me.NoteMessage;
                textBoxPresence.Text = this.UcwaApp.Me.PresenceAvailability;
                var phones = this.UcwaApp.Me.PhoneLines;
                foreach (var phone in phones)
                    textBoxPhones.Text += (string.IsNullOrEmpty(textBoxPhones.Text) ? "" : ", ") + phone.Type + ":" + phone.Number;
    
    
            }
    ```
    
    After signing in successfully, the local user data, including the display name, availability and phone numbers are displayed in the **MePage**. Make sure to insert the async keyword in the method signature above, because the async/await asynchronous pattern is used to call the UCWA features.

4.  Add the class definition of SignInParameter to the namespace as follows.
    
    ```csharp
        public sealed class SignInParameter
        {
            internal string UserName { get; private set; }
            internal string Password { get; private set; }
            public SignInParameter(string name, string pass)
            {
                this.UserName = name;
                this.Password = pass;
            }
        }
    ```
    
    This helper class is used to pass the user name and password when the application navigates from **MainPage** to **MePage**. This navigation code is shown in the next step.

5.  Add the page navigation code to the button\_SignIn\_Clicked event handler in the MainPage.xaml.cs.
    
    ```csharp
            private void buttonSignIn_Clicked(object sender, RoutedEventArgs e)
            {
                // Navigate to the MePage
                this.Frame.Navigate(typeof(MePage), new SignInParameter(textBoxUserName.Text, passwordBox.Password));
            }
    ```
    
    When the **Sign In** button is clicked, the **MePage** will be loaded. User-entered user name and password will be passed along.

This concludes our UCWA **Hello, World\!** app for Windows Store. It covers a simple, but self-contained app development process for building a UCWA Windows Store application using C\#/XAML/XML. I hope this introduction provides you with a starting point to explore further the design and development of UCWA apps for Windows Store.

## See also

  - [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md)

  - [Create a UCWA Windows Store app project](create-a-ucwa-windows-store-app-project.md)

  - [Enable fluid user interface](enable-fluid-user-interface.md)

  - [Ensure responsive HTTP operations](ensure-responsive-http-operations.md)

  - [Implement the UCWA sign-in workflow](implement-the-ucwa-sign-in-workflow.md)

## See also

#### Other resources

[Create a UCWA Windows Store app using C\#/XAML and XML](http://code.msdn.microsoft.com/create-a-ucwa-windows-2c48d3f9)

