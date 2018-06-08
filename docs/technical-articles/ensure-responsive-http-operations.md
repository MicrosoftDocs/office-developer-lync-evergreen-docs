---
title: Ensure responsive HTTP operations
TOCTitle: Ensure responsive HTTP operations
ms:assetid: d36fff17-9edf-44c0-b52f-d6b36211142b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn551193(v=office.15)
ms:contentKeyID: 60829950
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Ensure responsive HTTP operations

**Applies to:** Lync 2013 | Lync Server 2013

In this section we walk through the steps to make asynchronous HTTP requests to access UCWA resources. Windows Store apps require asynchronous calls to ensure their responsiveness and uses the new (async/await) asynchronous programming pattern. The HTTP operations are implemented using the System.Net namespace.

## Enable responsive app through asynchronous programming patterns

1.  In **Solution Explorer**, right click the **WinStoreUcwaAppHello** project to select the **Add** INVALID USE OF SYMBOLS**Class** menu item.

2.  In the **Add New Item** pop-up window, change the class name to "Transport.cs".

3.  In the Transport.cs file, add the following using statements to the existing using statement block and the class to the public scope.
    
    ```csharp
    using System.Net;
    using System.IO;
    ```
    
    The modified class definition now looks as follows.
    
    ```csharp    
        using System;
        using System.Collections.Generic;
        using System.Linq;
        using System.Text;
        using System.Threading.Tasks;
        
        using System.Net;
        using System.IO;
        
        namespace WinStoreUcwaAppHello
        {
            public class Transport
            {
            }
        }
    ```
4.  Add the following code to implement general HTTP request submission operations.
    
    ```csharp
            private async Task<HttpWebResponse> SubmitRequest(string uri, string method, 
                                          KeyValuePair<string, string>[] requestHeaders, string requestData)
            {
                var request = await this.CreateRequest(uri, method, requestHeaders, requestData);
                var response = await this.GetResponse(request);
                return response;
            }
    ```
    
    This SubmitRequest method is an asynchronous call. The use of the async keyword in the method signature is necessary because awaitable calls are made using the await pattern from within the method. As an example, the method parameter takes a string value of "GET", "POST", "PUT" and "DELETE". The implementation involves calling two helper methods, CreateRequest and GetResponse. Both are asynchronous operations as well. An implementation of these and other related helper methods are shown in the following code listing.
    
    ```csharp
            private async Task<HttpWebRequest> CreateRequest(string url, string method, KeyValuePair<string, string>[] requestHeaders, string requestBody)
            {
                var fullUrl = this.ConvertToFullHttpUrl(url);
                var request = HttpWebRequest.CreateHttp(fullUrl);
    
                request.Method = method;
                request.Accept = this.ContentType;
                request.ContentType = this.ContentType;
                if (!string.IsNullOrEmpty(this.OAuthToken))
                    request.Headers["Authorization"] = this.OAuthToken;
    
                // Set the supplied headers, if any.
                if (requestHeaders != null)
                    foreach (var header in requestHeaders)
                        request.Headers[header.Key] = header.Value;
    
                // Set the supplied body, if any.
                if (!string.IsNullOrEmpty(requestBody))
                {
                    UTF8Encoding encoding = new UTF8Encoding();
                    byte[] body = encoding.GetBytes(requestBody);
                    var reqStream = await this.GetRequestStream(request);
                    reqStream.Write(body, 0, body.Length);
                    reqStream.Flush();
                }
                return request;
            }
            // Asynchronous method to get request stream
            private Task<Stream> GetRequestStream(HttpWebRequest request)
            {
                Stream requestStream;
                var taskComplete = new TaskCompletionSource<Stream>();
                request.BeginGetRequestStream(asyncRequest =>
                {
                    try
                    {
                        HttpWebRequest responseRequest = (HttpWebRequest)asyncRequest.AsyncState;
                        requestStream = (Stream)responseRequest.EndGetRequestStream(asyncRequest);
                        taskComplete.TrySetResult(requestStream);
                    }
                    catch (WebException ex)
                    {                    
                        Utils.ReportError(HttpStatusCode.BadRequest, ex.Message + "\r\n" + ex.StackTrace);
                    }
                }, request);
                return taskComplete.Task;
            }
            // Asynchronous method to get a request's response.
            private Task<HttpWebResponse> GetResponse(HttpWebRequest request)
            {
                HttpWebResponse response;
                var taskComplete = new TaskCompletionSource<HttpWebResponse>();
                request.BeginGetResponse(asyncResponse =>
                {
                    try
                    {
                        HttpWebRequest responseRequest = (HttpWebRequest)asyncResponse.AsyncState;
                        response = (HttpWebResponse)responseRequest.EndGetResponse(asyncResponse);
                        taskComplete.TrySetResult(response);
                    }
                    catch (WebException ex)
                    {
                        response = (HttpWebResponse)ex.Response;
                        taskComplete.TrySetResult(response);
                    }
                }, request);
                return taskComplete.Task;
            }
            private string ConvertToFullHttpUrl(string uri)
            {
                return uri == null || uri.StartsWith("http") ? uri : "https://" + this.Host + uri;
            }
    ```

5.  Add the following code as part of the Transport class definition to provide public-facing and method-specific HTTP request operations. The four methods (GetRequest, PostRequest, PutRequest and DeleteRequest) correspond to the HTTP GET, POST, PUT and DELETE operations supported in UCWA.
    
    ```csharp
            #region public-facing method-specific asynchronous request submissions, including GET, POST, PUT and DELETE
            private async Task<HttpWebResponse> GetRequest(string uri, params KeyValuePair<string, string>[] requestHeaders)
            {
                return await this.SubmitRequest(uri, "GET", requestHeaders, null);
            }
            private async Task<HttpWebResponse> PostRequest(string uri, string requestData, params KeyValuePair<string, string>[] requestHeaders)
            {
                return await this.SubmitRequest(uri, "POST", requestHeaders, requestData);
            }
            private async Task<HttpWebResponse> PutRequest(string uri, string requestData, params KeyValuePair<string, string>[] requestHeaders)
            {
                return await this.SubmitRequest(uri, "PUT", requestHeaders, requestData);
            }
    
            private async Task<HttpWebResponse> DeleteRequest(string uri)
            {
                return await this.SubmitRequest(uri, "DELETE", null, null);
            }
            #endregion method-specific request submissions
    ```

6.  Add the following code to complete the class definition. They include the class constructor and a few public properties. By default, this transport works message payloads of the XML format. A caller of this class may override the content type by setting the ContentType property.
    
    ```csharp 
            public Transport()
            {
                this.ContentType = "application/xml";
            }
            #region public properties
            public string ContentType { get; set; }
            public string Host { get; set; }
            public string OAuthToken { get; set; }
            #endregion public properties
    ```

When using the above Transport class to access UCWA resources, make sure that the OAuthToken properties is set whenever the user is authenticated or re-authenticated. If a relative Uri is used to specify a UCWA resource, the Host property must be set as well.

## See also

- [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md)
- [Create your first Windows Store app using C\# or Visual Basic](http://msdn.microsoft.com/en-us/library/windows/apps/hh974581.aspx)
- [Create a UCWA Windows Store app project](create-a-ucwa-windows-store-app-project.md)
- [Enable fluid user interface](enable-fluid-user-interface.md)
- [Implement the UCWA sign-in workflow](implement-the-ucwa-sign-in-workflow.md)
- [Putting it all together](putting-it-all-together.md)

