# Elastic integrations Docs


## [Microsoft Exchange Online Message Trace Integration](https://docs.elastic.co/integrations/microsoft_exchange_online_message_trace)

Microsoft Exchange Online Message Trace Integration

This integration receives logs over the [Microsoft Exchange Online Message Trace API](https://learn.microsoft.com/en-us/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15)) or read from a log file.


### Configuring with OAuth2

The basic authentication configuration fields have been removed from this integration as Microsoft has deprecated and disabled basic authentication for Exchange Online. See the [deprecation notification](https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online) for details. In order to continue using the Microsoft Exchange Online Message Trace you will need to enable and configure OAuth2 authentication.

Steps to register an [Azure AD application](https://learn.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app):



1. Go to the Azure portal (https://portal.azure.com/) and sign in.
2. Click on “Azure Active Directory” in the left-hand menu.
3. Select “App registrations” and click “New registration”.
4. Enter a name for your application, select “Accounts in this organisational directory only” for “Supported account types”,
5. Click “Register” to create the application.
6. On the application page, make note of the “Application (client) ID” (which is your client ID) and the “Directory (tenant) ID” (which is your tenant ID).
7. Under “Certificates & secrets”, click “New client secret” to create a new secret. Make note of the secret value (which is your client secret).
8. Add [API permissions](https://learn.microsoft.com/en-us/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15)#specify-the-permissions-your-app-requires-to-access-the-reporting-web-service) (**Application Permissions**) and request/grant admin consent:
    1. Office 365 Exchange online
        * ReportingWebService.Read.All
9. Add API permissions  (**Delegated Permissions**) and request/grant admin consent:
    2. Microsoft Graph
        * User.read
    3. Office 365 Exchange online
        * ReportingWebService.Read.All

API permissions sample



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")


[Role assignment](https://learn.microsoft.com/en-us/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15)#assign-azure-ad-roles-to-the-application) : 



1. [https://portal.azure.com/#home](https://portal.azure.com/#home)
2. Azure Active Directory -> Roles & administrators -> **Global Reader**
3. Add assignments your created app
4. Azure Active Directory -> Roles & administrators -> ** Security Reader**
5. Add assignments your created app


### Integration Configuration:

**URL:** https://reports.office365.com/ecp/reportingwebservice/reporting.svc/MessageTrace

**Client ID, Client Secret, Tenant ID:** values noted from the previous step.

**Request Timeout:** 60s (default) you have to take into consideration the initial interval time as it can affect the api fetch time. 

**Oauth2 Scopes:** [https://outlook.office365.com/.default](https://outlook.office365.com/.default)

**OAuth Token Endpoint: **oauth2/v2.0/token

Integration Configuration sample



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")


Dashboard sample



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



### Appendix 


#### Some errors from misconfiguration or lack of permissions

[elastic_agent.filebeat][error] Error while processing http request: failed to execute rf.collectResponse: failed to execute http client.Do: failed to execute http client.Do: failed to read http.response.body: Get "https://reports.office365.com/ecp/reportingwebservice/reporting.svc/MessageTrace?%24filter=StartDate+eq+datetime%272023-05-14T13%3A10%3A06Z%27+and+EndDate+eq+datetime%272023-05-14T14%3A10%3A06Z%27&%24skiptoken=0": Post "/213f3c00-6fc5-44ad-bef2-1467a1h18530/": Post "/213f3c00-6fc5-44ad-bef2-1467a1h18530/": unsupported protocol scheme ""

10:14:30.796

elastic_agent.filebeat

[elastic_agent.filebeat][error] Error while processing http request: failed to execute rf.collectResponse: failed to execute http client.Do: failed to execute http client.Do: failed to read http.response.body: Get "https://reports.office365.com/ecp/reportingwebservice/reporting.svc/MessageTrace?%24filter=StartDate+eq+datetime%272023-05-14T23%3A14%3A29Z%27+and+EndDate+eq+datetime%272023-05-15T00%3A14%3A29Z%27&%24skiptoken=0": oauth2: cannot fetch token: 400 Bad Request

Response: {"error":"invalid_resource","error_description":"AADSTS500011: The resource principal named https://reports.office365.com/ecp/reporting was not found in the tenant named xyz comp. This can happen if the application has not been installed by the administrator of the tenant or consented to by any user in the tenant. You might have sent your authentication request to the wrong tenant.\r\nTrace ID: 213f3c00-6fc5-44ad-bef2-1467a1h18530\r\nCorrelation ID: 213f3c00-6fc5-44ad-bef2-1467a1h18530\r\nTimestamp: 2023-05-15 00:14:30Z","error_codes":[500011],"timestamp":"2023-05-15 00:14:30Z","trace_id":"213f3c00-6fc5-44ad-bef2-1467a1h18530","correlation_id":"ee1a4db6-4f7c-430b-aadd-06f161ffd39","error_uri":"https://login.microsoftonline.com/error?code=500011"}


#### Elastic integrations code owners (who to reach out to)

[https://github.com/elastic/integrations/blob/main/.github/CODEOWNERS](https://github.com/elastic/integrations/blob/main/.github/CODEOWNERS)


#### Elastic integration Github:

[https://github.com/elastic/integrations/tree/main/packages/microsoft_exchange_online_message_trace](https://github.com/elastic/integrations/tree/main/packages/microsoft_exchange_online_message_trace)
