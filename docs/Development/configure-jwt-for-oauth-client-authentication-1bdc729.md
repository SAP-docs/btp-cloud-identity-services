<!-- copy1bdc7291de0e4e529648bfe05856029a -->

# Configure JWT for OAuth Client Authentication

Configure the issuer and subject of tokens for JSON Web Token \(JWT\) client authentication in token requests to OpenID Connect applications.



<a name="copy1bdc7291de0e4e529648bfe05856029a__prereq_lz2_wxt_1tb"/>

## Prerequisites

-   You have an OpenID Connect application.
-   You have created and configured a corporate identity provider of type *OpenID Connect Compliant* in the administration console for Identity Authentication. For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](../Operation-Guide/configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).




## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](../Operation-Guide/create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Application APIs*, choose *Client Authentication*.

6.  Choose the *Add* button in the *JSON Web Tokens* section.

7.  Provide the required info in the popup.


    <table>
    <tr>
    <th valign="top">

     


    
    </th>
    <th valign="top">

     


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    **Description**


    
    </td>
    <td valign="top">

    This field is optional. You can provide information about the token here.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Issuer**


    
    </td>
    <td valign="top">

    The issuer is a corporate identity provider of type *OpenID Connect Compliant*. It must be created and configured in the administration console first.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Subject**


    
    </td>
    <td valign="top">

    The sub \(subject\) that is expected in the token.

    > ### Tip:  
    > If you want to use an OAuth 2.0 token from Microsoft Azure AD as client credentials for an OpenID Connect application in Identity Authentication, and your OAuth client in Azure AD belongs to an Enterprise Application, the subject in the token is the Object ID of the Enterprise Application.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Scope**


    
    </td>
    <td valign="top">

    > ### Note:  
    > This section is read-only. The predefined choice is OpenID.


    
    </td>
    </tr>
    </table>
    
8.  Save your configuration.


**Related Information**  


[Configure Secrets for API Authentication](configure-secrets-for-api-authentication-9ea13fe.md "This document describes how developers configure secrets with scopes and validity for client authentication.")

[Unlock Client ID](unlock-client-id-e5a6b85.md "Unlock the client ID after five failed logon attempts before the automatic unlock time of 60 minutes has passed.")

[Disable Client ID Locking](disable-client-id-locking-aa38152.md "You can disable the automatic lock of the client ID after five failed logon attempts.")

[Configure Certificates for API Authentication](configure-certificates-for-api-authentication-47e9866.md "This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.")

[SCIM REST API Authentication Mechanisms](scim-rest-api-authentication-mechanisms-e3f31bd.md "See how to configure the authentication mechanisms for the SCIM REST API methods of Identity Authentication.")

