<!-- copyaa381523af6140feaa2ee8ffb5929d5c -->

# Disable Client ID Locking

You can disable the automatic lock of the client ID after five failed logon attempts.



## Context

By default the client ID locks for 60 minutes after five failed logon attempts.

You can disable the automatic lock of the client ID via the administration console for SAP Cloud Identity Services. Use this option to disable the automatic lock in cases when the client ID has a limited scope and the client ID secret\(s\) are automatically generated.

> ### Note:  
> When you disable the *Client ID Lock* option for a client ID that is already locked, this resets the failed logon attempts counter but the client ID remains unlocked. If you want to unlock the client ID before the automatic unlock time of 60 minutes has passed you must unlock it manually. For more information, see [Unlock Client ID](../Operation-Guide/unlock-client-id-665b9e0.md).

"

To disable the *Client ID Lock* option, follow the procedure below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

4.  Under *API AUTHENTICATION*, choose *Client ID and Secrets*.

5.  Disable the *Client ID Lock*.

    If the operation is successful, you receive the following message: ***Client ID locking updated.***. The slider next to *Client ID Lock* is switched to *OFF*.

    > ### Note:  
    > If you want to enable client ID password locking for the application, drag the slider to *ON*.


**Related Information**  


[Configure Secrets for API Authentication](configure-secrets-for-api-authentication-9ea13fe.md "This document describes how developers configure secrets with scopes and validity for client authentication.")

[Unlock Client ID](unlock-client-id-e5a6b85.md "Unlock the client ID after five failed logon attempts before the automatic unlock time of 60 minutes has passed.")

[Configure Certificates for API Authentication](configure-certificates-for-api-authentication-47e9866.md "This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.")

[Configure JWT for OAuth Client Authentication](configure-jwt-for-oauth-client-authentication-1bdc729.md "Configure the JSON Web Token (JWT) - the issuer and subject of tokens for JWT client authentication in token requests, or the URI for JSON web key retrieval for client authentication.")

[SCIM REST API Authentication Mechanisms](scim-rest-api-authentication-mechanisms-e3f31bd.md "See how to configure the authentication mechanisms for the SCIM REST API methods of Identity Authentication.")

