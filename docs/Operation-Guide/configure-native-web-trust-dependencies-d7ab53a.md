<!-- loiod7ab53a5e934456f931b5deca7703c44 -->

# Configure Native-Web Trust Dependencies

Enable a native or mobile application to hand off an authenticated session to a web application without requiring the user to log in again.



## Prerequisites

-   The native application has the token exchange grant type enabled \(`urn:ietf:params:oauth:grant-type:token-exchange`\).
-   The native application has an active refresh token for the authenticated user.
-   You know the name of the target web application in your SAP Cloud Identity Services tenant.



## Context

Use native-web trust dependencies when a user is already authenticated in a native or mobile application and needs to open a web application in a browser. Without this configuration, the browser has no active session and prompts the user to log in again. With this configuration, the native application exchanges its refresh token for a short-lived, one-time SSO token. This SSO token is then passed to the `/saml2/idp/sso` endpoint of the SAP Cloud Identity Services tenant, which establishes a web session for the user and redirects the browser to the target application without a login prompt.

An application can have up to 20 native-web trust dependencies.

After you configure the trust dependency, the native application can obtain an SSO token and use it to open a web session. The following information is done by the developer and provided for context.

1.  The native application exchanges the refresh token for an SSO token.

    ```
    POST https://<tenant>.accounts.ondemand.com/oauth2/token
    Content-Type: application/x-www-form-urlencoded
    grant_type=urn:ietf:params:oauth:grant-type:token-exchange
    &client_id=<client-id>
    &client_secret=<client-secret>
    &subject_token=<refresh-token>
    &subject_token_type=urn:ietf:params:oauth:token-type:refresh_token
    &resource=urn:sap:identity:sso
    ```

    The response is an opaque access token valid for five minutes. When introspected, it contains:

    -   `sso_application_ids`: the application IDs of the originating application and all configured Native-Web Trust target applications.

    -   `sso_redirect_uris`: the trusted redirect URIs derived from all trusted applications.


2.  The native application passes the SSO token and the intended redirect URI to the browser:

    <code>https://<i class="varname">&lt;tenant&gt;</i>.accounts.ondemand.com/saml2/idp/sso?sso_token=<i class="varname">&lt;sso-token&gt;</i>&amp;redirect_uri=<i class="varname">&lt;trusted-uri&gt;</i></code>

    The SAP Cloud Identity Services tenant validates the SSO token, creates a web session for the user, and redirects the browser to the specified URI. The user arrives at the target web application already authenticated.

    > ### Note:  
    > The `redirect_uri` value must be one of the trusted redirect URIs included in the SSO token. Requests with an untrusted redirect URI are rejected.




## Procedure

1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*.

2.  Choose the native application \(the originating application running on the device\).

3.  Choose the *Trust* tab.

4.  Under *Application APIs*, choose *Dependencies*.

5.  Choose *Native-Web Trust*.

6.  Choose *Add* and select the target web application.

7.  Save your entries.




## Results

The native-web trust dependency is established. When the native application performs a token exchange with `resource=urn:sap:identity:sso`, the issued SSO token includes the application ID of the configured target web application in its `sso_application_ids` claim and the trusted redirect URIs of that application in its `sso_redirect_uris` claim. The user can move from the native application to the web application in a browser without being prompted to log in.



## Next Steps

After the SSO flow completes, the user is redirected to a trusted URI. For OIDC applications, the configured redirect URIs are used. For SAML applications, the SSO endpoints are used. For both application types, the home URL is also included. To add a specific post-SSO redirect destination, configure the home URL of the target application.

> ### Note:  
> The web session is always established with the `/saml2/idp/sso` endpoint, regardless of whether the target application uses SAML or OIDC.

