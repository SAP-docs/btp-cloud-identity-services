<!-- copye5a6b85658f74a508eacc137382599df -->

# Unlock Client ID

Unlock the client ID after five failed logon attempts before the automatic unlock time of 60 minutes has passed.



## Context

The client ID locks for 60 minutes after five failed logon attempts. After 60 minutes the client ID is automatically unlocked.

To unlock the client ID before the automatic unlock time of 60 minutes has passed follow the procedure below:



<a name="copye5a6b85658f74a508eacc137382599df__steps_nyj_331_zlb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

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

[Configure JWT for OAuth Client Authentication](configure-jwt-for-oauth-client-authentication-1bdc729.md "Configure the JSON Web Token (JWT) - the issuer and subject of tokens for JWT client authentication in token requests, or the URI for JSON web key retrieval for client authentication.")

[Disable Client ID Locking](../Operation-Guide/disable-client-id-locking-f1dc77e.md "You can disable the automatic lock of the client ID after five failed logon attempts.")

