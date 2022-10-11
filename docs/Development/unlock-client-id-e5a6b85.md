<!-- copye5a6b85658f74a508eacc137382599df -->

# Unlock Client ID

Unlock the client ID after five failed logon attempts before the automatic unlock time of 60 minutes has passed.



## Context

The client ID locks for 60 minutes after five failed logon attempts. After 60 minutes the client ID is automatically unlocked.

To unlock the client ID before the automatic unlock time of 60 minutes has passed follow the procedure below:



<a name="copye5a6b85658f74a508eacc137382599df__steps_nyj_331_zlb"/>

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

3.  Choose the application with a locked client ID.

4.  Under *API AUTHENTICATION*, choose *Client ID and Secrets*.

5.  Choose *Unlock* next to *Client ID Status*.

    > ### Remember:  
    > You can only unlock locked client IDs. If the client ID is not locked, the *Unlock* button is disabled.


**Related Information**  


[Configure Secrets for API Authentication](configure-secrets-for-api-authentication-9ea13fe.md "This document describes how developers configure secrets with scopes and validity for client authentication.")

[Disable Client ID Locking](disable-client-id-locking-aa38152.md "You can disable the automatic lock of the client ID after five failed logon attempts.")

[Configure Certificates for API Authentication](configure-certificates-for-api-authentication-47e9866.md "This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.")

[Configure JWT for OAuth Client Authentication](configure-jwt-for-oauth-client-authentication-1bdc729.md "Configure the issuer and subject of tokens for JSON Web Token (JWT) client authentication in token requests to OpenID Connect applications.")

[SCIM REST API Authentication Mechanisms](scim-rest-api-authentication-mechanisms-e3f31bd.md "See how to configure the authentication mechanisms for the SCIM REST API methods of Identity Authentication.")

[Disable Client ID Locking](../Operation-Guide/disable-client-id-locking-f1dc77e.md "You can disable the automatic lock of the client ID after five failed logon attempts.")

