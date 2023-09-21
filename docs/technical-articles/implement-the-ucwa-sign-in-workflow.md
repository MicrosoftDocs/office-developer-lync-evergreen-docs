---
title: Implement the UCWA sign-in workflow
TOCTitle: Implement the UCWA sign-in workflow
ms:assetid: 469cc626-0a73-4136-bab2-9bb024dd56c8
ms:mtpsurl: https://msdn.microsoft.com/library/Dn551191(v=office.15)
ms:contentKeyID: 60829951
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
- html
---

# Implement the UCWA sign-in workflow

**Applies to:** Lync 2013 | Lync Server 2013

Signing in to UCWA is the first step of any UCWA application. The process involves discovering the UCWA root resource, from which the user authentication can proceed. Once the user is authenticated, a UCWA application resource is created and bound to the local endpoint. These tasks are demonstrated in the steps below and implemented in a separate C\# class file (namely, UcwaApp.cs).

## Sign in to UCWA with specified user name and password

1.  Add a class to the Visual Studio project and name the new class UcwaApp.

2.  Add to the UcwaApp class definition the following DiscoverRootResource method that obtains the root resource of a specified user using the Lync auto discovery service.
    
    ```csharp
            private async Task<UcwaHttpOperationResult> DiscoverRootResource(bool discoverFromInternalDomain = false)
            {
                this.discoverFromInternalDomain = discoverFromInternalDomain;
                string domain = this.userName.Contains("@") ? this.userName.Split('@')[1] : null;
                this.discoverUrl = "https://lyncdiscoverinternal." + domain;
                if (!this.discoverFromInternalDomain)
                    this.discoverUrl = "https://lyncdiscover." + domain;
    
                var opResult = await GetRootResource(this.discoverUrl, maxDiscoverTrials);
                if (opResult.Resource == null)
                {
                    if (this.discoverFromInternalDomain)
                    {
                        this.discoverUrl = "https://lyncdiscover." + domain;
                        this.InternalDomain = false;
                        opResult = await GetRootResource(this.discoverUrl, maxDiscoverTrials);
                    }
                    if (opResult.Resource == null)
                        return opResult;
                }
                if (discoverUrl.ToLower().Contains("lyncdiscoverinternal"))
                    this.InternalDomain = true;
                else
                    this.InternalDomain = false;
    
                string redirectUrl = opResult.Resource.GetLinkUri("redirect");
                if (!string.IsNullOrEmpty(redirectUrl) && RedirectUrlSecurityCheckPassed(redirectUrl))
                {
                    opResult = await GetRedirectResource(redirectUrl);
                }
                return opResult;
            }
    ```
    
    Typically, the auto discovery process starts with obtaining the user’s root resource using the internal UCWA service as identified by the Url of the https://lyncdiscoverinternal.\<domain\> form, where \<domain\> stands for the user domain as parsed from the input user name of the user@domain format. When the internal service is not enabled, no root resource is returned. In this case, the process continues to the external UCWA service that is identified by the Url of this form: https://lyncdiscover.\<domain\>.
    
    Given a Lync discovery service Url, the steps to get the root resource may be implemented as follows.
    
    ```csharp
            private async Task<UcwaHttpOperationResult> GetRootResource(string url, int maxTrials = 3)
            {
                HttpWebResponse response;
                UcwaResource resource = null;
                int trials = 0;
                while (trials < maxTrials)
                {
                    trials++;
                    response = await Transport.GetRequest(url);
                    if (response != null && response.StatusCode == HttpStatusCode.OK)
                    {
                        resource = new UcwaResource(response.GetResponseStream());
                        return new UcwaHttpOperationResult(response.StatusCode, null, resource);
                    }
                }
                return new UcwaHttpOperationResult(HttpStatusCode.NotFound, "Failed to get root resource of " + url);
            }
    ```
    
    If the specified user is homed on a different server pool, a redirect resource will be returned. You must repeat the steps above to get the root resource using the redirected Url. Before doing that, you should make sure that the supplied redirect Url passes appropriate security checks. For more information on security checks on a redirect Url, see [Getting Started to Using UCWA](http://ucwa.skype.com/documentation/gettingstarted-rooturl). As an illustration, the work flow to get redirected root resource is shown in the following GetRedirectResource method.
    
    ```csharp
            private async Task<UcwaHttpOperationResult> GetRedirectResource(string redirectUrl, bool checkRedirectUrl = true)
            {
                if (checkRedirectUrl && !RedirectUrlSecurityCheckPassed(redirectUrl))
                {
                    return new UcwaHttpOperationResult(HttpStatusCode.Redirect, "Failed to pass security check on redirect of " + redirectUrl);
                }
                var response = await Transport.GetRequest(redirectUrl);
                if (response.StatusCode != HttpStatusCode.OK)
                    return new UcwaHttpOperationResult(response.StatusCode, UcwaAppUtils.ConvertResponseBodyStreamToString(response.GetResponseStream()));
                try
                {
                    var res = new UcwaResource(response.GetResponseStream());
                    return new UcwaHttpOperationResult(response.StatusCode, null, res);
                }
                catch (Exception e)
                {
                    return new UcwaHttpOperationResult(response.StatusCode, e.Message, null, e);
                }
            }
    ```
    
    Here, the raw UCWA resource (in XML) is encapsulated in the UcwaResource class. Its implementation is shown in the Create a wrapper class to parse UCWA resources in XML section.

3.  Add to the UcwaApp class definition the following GetUserResource method that authenticates the user and obtains an OAuth token required of the subsequent HTTP requests.
    
    ```csharp
            private async Task<UcwaHttpOperationResult> GetUserResource(string userResUri, string userName, string password, AuthenticationTypes authType = AuthenticationTypes.Password)
            {
                this.IsSignedIn = false;
                //
                // First GET user resource to retrieve oAuthToken href. 
                // Expect 401 Unauthorized response as an HTML payload
                var response = await Transport.GetRequest(userResUri);
                if (response.StatusCode != HttpStatusCode.Unauthorized && response.StatusCode != HttpStatusCode.OK)
                {
                    return new UcwaHttpOperationResult(response.StatusCode, "Failed to GetRequest on " + userResUri);
                }
    
                if (response.StatusCode == HttpStatusCode.Unauthorized)
                {
                    // Get OAuth resource for a Web ticket
                    var authHeader = UcwaAppUtils.ConvertWebHeaderCollectionToKeyValuePairs(response.Headers)
                        .Where(a => a.Key == "WWW-Authenticate" && a.Value.Contains("MsRtcOAuth href"))
                        .FirstOrDefault().Value;
                    var oAuthHref = authHeader.Split(',').Where(s => s.Contains("MsRtcOAuth")).FirstOrDefault()
                        .Split('=')[1].Replace("\"", "").Trim();
                    string requestBody = GetAuthenticationRequestBody(userName, password, authType);
    
                    // Note: the following PostRequest returns a json payload in the responseData, containing the access token, 
                    var cType = "application/x-www-form-urlencoded;charset='utf-8'";
                    var aType = "application/x-www-form-urlencoded;charset='utf-8'";
    
                    response = await Transport.PostRequest(oAuthHref, aType, cType, requestBody);
                    if (response.StatusCode != HttpStatusCode.OK)
                        return new UcwaHttpOperationResult(response.StatusCode, "PostRequest on " + oAuthHref + " with " + requestBody);
    
                    string responseData = UcwaAppUtils.ConvertResponseBodyStreamToString(response.GetResponseStream());
    
                    if (authType == AuthenticationTypes.Passive && response.StatusCode == HttpStatusCode.BadRequest &&
                        responseData.Contains("ms_rtc_passiveauthuri"))
                    {
                        // get ms_rtc_passiveauthuri to obtain an ADFS cookie and do another POST request (above) to obtain UCWA oAuth token
                        System.Text.RegularExpressions.Regex regex = new System.Text.RegularExpressions.Regex("\"ms_rtc_passiveauthuri\":\"(.)\"");
                        var match = regex.Match(responseData);
                        var passiveauthuri = match.Groups[1].Value;
                        // to do: obtain a token from ADFS
                        //    ... .// omitted here
    
                        // repost on oAuthHref, once a new ADFS token is had
                        response = await Transport.PostRequest(oAuthHref, aType, cType, requestBody);
                        if (response.StatusCode != HttpStatusCode.OK)
                            return new UcwaHttpOperationResult(response.StatusCode, "PostRequest on " + oAuthHref + " with " + requestBody);
                        responseData = UcwaAppUtils.ConvertResponseBodyStreamToString(response.GetResponseStream());
                    }
    
                    // Extract the access token from the response body to construct the oAuth token
                    oAuth20Token = GetOAuthToken(responseData);
                    if (oAuth20Token != null)
                    {
                        Transport.OAuthToken = oAuth20Token;
                        // Second GET userHref, supplying the required compact-web-ticket (cwt) in an Authorization header
                        response = await Transport.GetRequest(userResUri);
                        if (response.StatusCode != HttpStatusCode.OK)
                            return new UcwaHttpOperationResult(response.StatusCode, "GetRequest on " + userResUri + " with oAuth token of " + oAuth20Token);
                    }
                    else
                    {
                        return new UcwaHttpOperationResult(response.StatusCode, "PostRequest on " + oAuthHref + " returns " + responseData);
                    }
                }
                this.IsSignedIn = true;
                var res = new UcwaResource(response.GetResponseStream());
                return new UcwaHttpOperationResult(response.StatusCode, null, res);
            }
    ```
    
    The first attempt to get the UCWA [user](http://ucwa.skype.com/documentation/resources-user) resource results in a 401 Unauthorized response. Its headers include one named WWW-Authenticate with a value similar to the following.
    
    ```html
    Bearer trusted_issuers="00000002-0000-0ff1-ce00-000000000000@contoso.com", client_id="00000004-0000-0ff1-ce00-000000000000",MsRtcOAuth href="https://lyncweb.contoso.com/WebTicket/oauthtoken",grant_type="urn:microsoft.rtc:windows,urn:microsoft.rtc:anonmeeting,password"
    ```
    
    Contained in this WWW-Authenticate header is the Uri of the OAuth token provider as specified by the MsRtcOAuth href parameter value, together with allowed authentication types as specified by the grant\_type parameter value. Here, a user can be authenticated using a Windows security credentials or password. If enabled, a user can also anonymously join a meeting. To continue, the href value, parsed into the oAuthHref variable. A POST request is then submitted against this Uri, together with the user name and password specified as the payload of the request.
    
    The response from the MsRtcOAuth provider contains the required oAuth token for the user in the response body, an example of which is shown as follows.
     
     `{"access_token":"cwt=AAEBHAEFAAAAAAAFFQAAAIxVppb2z4Dxaju2058FAACBEPoG3XyftjBYhE5zTT0buHeCAotbgyDsTGw1VRfC0jPIQlfoa9VU-7UZoTtyNvTaXSKdEGRMToYI85tyCISt0AgNEPoG3XyftjBYhE5zTT0buHc","expires_in":27402,"ms_rtc_identityscope":"local","token_type":"Bearer"}`
    
    Because the authentication service responds in JSON, the data can be parsed using the Windows.Data.Json namespace. This is shown in the following subroutine.
    
    ```csharp
            private string GetOAuthToken(string responseData)
            {
                string oAuth20Token = null;
                Windows.Data.Json.JsonObject json;
                if (Windows.Data.Json.JsonObject.TryParse(responseData, out json))
                    if (json.ContainsKey("access_token") && json.ContainsKey("token_type"))
                    {
                        var at = json.GetNamedValue("access_token");
                        var tt = json.GetNamedValue("token_type");
                        if (at != null && tt != null)
                            oAuth20Token = tt.GetString() + " " + at.GetString();
                    }            
                return oAuth20Token;
            }
    ```
    
    The corresponding OAuth ticket is constructed as follows,
    
    ```json
        Bearer cwt=AAEBHAEFAAAAAAAFFQAAAIxVppb2z4Dxaju2058FAACBEPoG3XyftjBYhE5zTT0buHeCAotbgyDsTGw1VRfC0jPIQlfoa9VU-7UZoTtyNvTaXSKdEGRMToYI85tyCISt0AgNEPoG3XyftjBYhE5zTT0buHc
    ```
    And it's then set as the Authorization header value for the next GET HTTP request against the user resource. This time, the HTTP request should return a status of OK.

4.  Add to the UcwaApp class definition the following GetApplicationResource method that creates and returns an application resource bound to the local endpoint of the specified user.
    
    ```csharp
            /// <summary>
            /// Get an application resource bound to the user's local endpoint
            /// </summary>
            /// <param name="resUser">The authenticated user resource</param>
            /// <param name="userAgent">The name of this application</param>
            /// <param name="culture">The locale of this application</param>
            /// <returns>The application resource as part of UcwaHttpOperationResult</returns>
            async Task<UcwaHttpOperationResult> GetApplicationResource(UcwaResource resUser,
                string userAgent = "ContosoApp/1.0 (WinStore)", string culture = "en-us")
            {
                applicationsUrl = resUser.GetLinkUri("applications");
                Transport.Host = applicationsUrl.Split('/')[2];
    
                var endpointId = Guid.NewGuid().ToString();
                string appSettings = string.Format(appSettingsFormatter, culture, endpointId, userAgent);
                var response = await Transport.PostRequest(applicationsUrl, appSettings);
                if (response.StatusCode != HttpStatusCode.Created)
                    return new UcwaHttpOperationResult(response.StatusCode, "Failed to PostRequest on " + applicationsUrl);
    
                var res = new UcwaResource(response.GetResponseStream());
                return new UcwaHttpOperationResult(response.StatusCode, "CreateApplicationResource", res);
            }
    ```
    
    The operations involve parsing an authenticated user resource to obtain the applications resource, submitting a POST request on the applications resource to create an application resource, and processing the corresponding HTTP response to obtain the resultant [application](http://ucwa.skype.com/documentation/resources-application) resource, which will serve as the starting point for the current application to use all other UCWA features.
    
    Throughout the application life cycle, you may need to get an updated application resource when the underlying states change. This can be done by submitting an HTTP GET request against the cached application Url. An implementation of this process is shown as follows.
    
    ```csharp
            /// <summary>
            /// An overloaded member to get updated application resource, given the application uri.
            /// </summary>
            /// <param name="appUri">previously returned application uri</param>
            /// <returns>application resource as part of the UcwaHttpOperationResult</returns>
            public async Task<UcwaHttpOperationResult> GetApplicationResource(string appUri)
            {
                var response = await Transport.GetRequest(appUri);
                var res = new UcwaResource(response.GetResponseStream());
                return new UcwaHttpOperationResult(response.StatusCode, "GetUpdatedApplicationResource", res);
            }
    ```

5.  Add to the UcwaApp class definition the following SignIn method that implements the workflow to log the user by calling DiscoverRootResource, GetUserResource and then GetApplicationResource methods.
    
    ```csharp 
            public async Task<HttpStatusCode> SignIn(string userName, string password)
            {
                this.userName = userName;
                this.password = password;
                this.authenticationType = AuthenticationTypes.Password;
                try
                {
                    var opResult = await DiscoverRootResource(this.discoverFromInternalDomain);
                    if (opResult.Resource == null)
                    {
                        UcwaAppUtils.ReportProgress(OnProgressReported, "GetRootResource returns null result.", opResult.HttpStatusCode);
                        return opResult.HttpStatusCode;
                    }
    
                    opResult = await GetUserResource(opResult.Resource.GetLinkUri("user"), userName, password, this.authenticationType);
                    if (opResult.Resource == null)
                    {
                        UcwaAppUtils.ReportProgress(OnProgressReported,
                            userName + " cannot be authenticated, with the " + this.authenticationType.ToString() + " grant_type.",
                            opResult.HttpStatusCode);
                        return opResult.HttpStatusCode;
                    }
                    // Create the UCWA application bound to the specified user
                    opResult = await GetApplicationResource(opResult.Resource);
    
                    if (opResult.Resource == null)
                    {
                        UcwaAppUtils.ReportProgress(OnProgressReported, "Failed to create the UCWA application resource.", opResult.HttpStatusCode);
                        return opResult.HttpStatusCode;
                    }
    
                    this.ApplicationResource = opResult.Resource;
                    UcwaAppUtils.ReportProgress(OnProgressReported, "Succeeded in creating the application resource: " + this.ApplicationResource.Uri);
    
    
                    // Make me available to receive incoming alerts
                    this.Me = new UcwaAppMe(this);
                    var statusCode = await this.Me.PostMakeMeAvailable("4255552222", "Online",
                        new string[] { "Plain", "Html" }, new string[] { "PhoneAudio", "Messaging" });
                    if (statusCode != HttpStatusCode.NoContent)
                    {
                        UcwaAppUtils.ReportProgress(OnProgressReported, "Failed to post to makeMeAvailable resource.", statusCode);
                        return statusCode;
                    }
    
                    // Get application resource again to receive any updates triggered by the POST request to making me available
                    opResult = await GetApplicationResource(this.ApplicationResource.Uri);
                    if (opResult.Resource == null)
                    {
                        UcwaAppUtils.ReportProgress(OnProgressReported, "Failed to get the updated application resource", opResult.HttpStatusCode);
                        return opResult.HttpStatusCode;
                    }
                    this.ApplicationResource = opResult.Resource;
                    statusCode = await this.Me.Refresh();
    
                }
                catch (Exception ex)
                {
                    UcwaAppUtils.ReportError(OnErrorReported, ex);
                    return HttpStatusCode.BadRequest;
                }
                return HttpStatusCode.OK;
            }
    ```
    
    As the Password authentication will be used, this method takes as input the user name and password and returns HttpStatusCode to indicate the status of operation. The async keyword and the Task\<T\> return type are necessary to make the method asynchronous as a wait-able operation. In addition, the input userName and password values are cached for subsequent uses when the user must be authenticated again if the security token expires or the application disrupted.
    
    The sign-in process involves calling the DiscoverRootResource method (above) to get the root resource; calling the GetUserResource method (above) to authenticate the user and to obtain an OAuth token using the supplied user name and password; and then calling the GetApplicationResource method (above) to create and return an application resource. In each step, the resource targeted by next request is specified in the response of the current request.
    
    For a newly created UCWA application to receive incoming notifications, it must make the local user available to receive incoming notifications. This is done by issuing an HTTP POST request on the makeMeAvailable resource. (In this tutorial, the operation is exposed as the PostMakeMeAvailable method on the UcwaAppMe class encapsulating the me resource.) As a consequence, more resources become accessible to the application. You should get an updated application resource in order to access the newly available resources.

## See also

- [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md)
- [Create your first Windows Store app using C\# or Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh974581.aspx)
- [Create a UCWA Windows Store app project](create-a-ucwa-windows-store-app-project.md)
- [Enable fluid user interface](enable-fluid-user-interface.md)
- [Ensure responsive HTTP operations](ensure-responsive-http-operations.md)
- [Putting it all together](putting-it-all-together.md)

