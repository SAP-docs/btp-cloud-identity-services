<!-- loio5c3c35e01e3c4e7e8dd72af60c997c5d -->

# Configure Secrets for API Authentication

This document describes how developers configure secrets with scopes and validity for client authentication.



## Context

You can use a client ID and a secret to authenticate when REST API calls \(Invitation REST API, User management REST API, Password Service Rest API, and Forgot Password REST API\) to the tenant of Identity Authentication are used. The client ID and secret can also be used in the OpenID Connect scenarios of Identity Authentication.

The client ID is in the universally unique identifier \(UUID\) format. For example, `1ab7c243-5de5-4530-8g14-1234h26373ab`.

> ### Remember:  
> The User ID and a password \(secret\) to authenticate the client \(relying party\) in the OpenID Connect scenario must be encoded using the "application/x-www-form-urlencoded" encoding algorithm.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Application APIs*, choose *Client Authentication*.

    You can see the *Client ID* generated for the chosen application.

6.  Choose the *Add* button in the *Secrets* section.

7.  Provide the required info in the pop up.


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
    
    This field is optional.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Expire in**
    
    </td>
    <td valign="top">
    
    You can choose from three options:

    -   1 year
    -   2 years
    -   Never


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Scope**
    
    </td>
    <td valign="top">
    
    -   Application - Secrets with *Application* scope are used to update the Application configurations.
    -   Application Users - select this option to generate a secret to authenticate when REST API calls \(Invitation REST API, User management REST API, Password Service Rest API, and Forgot Service REST API\) are used.
    -   OpenID - select this option to generate a secret to authenticate in the OpenID Connect scenario.

    > ### Note:  
    > By default all options are selected. Your secret can be used for all scopes.


    
    </td>
    </tr>
    </table>
    
8.  Save your configuration.

    A pop up with the generated credentials appears. Make sure that you save the client secret for the client ID. You will need it for the API authentication, but you will not be able to retrieve it from the system later.




<a name="loio5c3c35e01e3c4e7e8dd72af60c997c5d__result_ngg_sqb_xkb"/>

## Results

Once your secret is generated you can see a table with your secrets and information about them. You can generate up to 20 client secrets per application.

**Related Information**  


[Unlock Client ID](unlock-client-id-665b9e0.md "Unlock the client ID after five failed logon attempts before the automatic unlock time of 60 minutes has passed.")

[Disable Client ID Locking](disable-client-id-locking-f1dc77e.md "You can disable the automatic lock of the client ID after five failed logon attempts.")

[Configure Certificates for API Authentication](configure-certificates-for-api-authentication-c408083.md "This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.")

[Configure JWT for OAuth Client Authentication](configure-jwt-for-oauth-client-authentication-db97a69.md "Configure the JSON Web Token (JWT) - the issuer and subject of tokens for JWT client authentication in token requests, or the URI for JSON web key retrieval for client authentication.")

[SCIM REST API Authentication Mechanisms](scim-rest-api-authentication-mechanisms-c599c89.md "See how to configure the authentication mechanisms for the SCIM REST API methods of Identity Authentication.")

