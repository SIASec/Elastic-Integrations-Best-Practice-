# Elastic integrations Docs


## [Microsoft 365 Integration](https://docs.elastic.co/integrations/o365)

Collect logs from Microsoft 365 with Elastic Agent.

Uses the [Office 365 Management Activity API](https://learn.microsoft.com/en-us/previous-versions/office/office-365-api/) to retrieve audit messages from Office 365 and Azure AD activity logs.

**Configuration**

To use this package you need to [enable Audit Log](https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-enable-disable?view=o365-worldwide) (if not already enabled) and register an application in Azure AD with the appropriate permissions.

Once this application is registered, note the:



* Application (client) ID 
* Directory (tenant) ID
* Then configure the authentication in the Certificates & Secrets section.

To use client-secret authentication, add your secret to the Client Secret (API key) field.

To use certificate-based authentication, set the paths to the certificate and private key files. If the key file is protected with a passphrase, set this passphrase in the Private key passphrase field. Paths must be absolute and files must exist in the host where Elastic Agent is running.

Steps to create an Azure AD application:



1. Go to the Azure portal (https://portal.azure.com/) and sign in.
2. Click on “Azure Active Directory” in the left-hand menu.
3. Select “App registrations” and click “New registration”.
4. Enter a name for your application, select “Accounts in this organisational directory only” for “Supported account types”,
5. Click “Register” to create the application.
6. On the application page, make note of the “Application (client) ID” (which is your client ID) and the “Directory (tenant) ID” (which is your tenant ID).
7. Under “Certificates & secrets”, click “New client secret” to create a new secret. Make note of the secret value (which is your client secret).
8. Add API permissions and request/grant admin consent:
    1. Microsoft Graph
        * User.read
    2. Office 365 Management API
        * ActivityFeed.Read
        * ActivityFeed.ReadDlp
        * ServiceHealth.Read

API Permissions sample



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")


Integration configuration Sample



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")


Dashboard Sample



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>
