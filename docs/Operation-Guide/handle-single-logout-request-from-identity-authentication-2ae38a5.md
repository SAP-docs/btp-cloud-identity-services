<!-- loio2ae38a527a3841b8839ed728cccdbf67 -->

# Handle Single Logout Request from Identity Authentication



When a user logs out from an application, the other applications that participate in the same user session must also be notified, so that it can log out the user as well. The application that does not trigger the logout, but must be notified, should do the following:

-   Provide own logout endpoint. For more information, see [OpenID Connect Front-Channel Logout 1.0](https://openid.net/specs/openid-connect-frontchannel-1_0.html#RPLogout).
-   Configure the endpoint \(Front-Channel Logout URIs\) in the respective Identity Authentication application. For more information, see [Configure OpenID Connect Application for Authorization Code Flow](configure-openid-connect-application-for-authorization-code-flow-4a94254.md) or [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow with PKCE](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-a721157.md).

    > ### Note:  
    > If the application is a multitenant one, it must include the tenant-specific logout endpoint during the login flow. This endpoint must follow the rules, specified in [Front-Channel Logout URI Rules](front-channel-logout-uri-rules-789c752.md). The logout endpoint is sent during login \(see[Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md) or [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow with PKCE](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-a721157.md)\).


**Related Information**  


[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

[Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services.")

[Configure Trusted Domains](configure-trusted-domains-08fa1fe.md "Service providers that delegate authentication to Identity Authentication can protect their applications when using embedded frames, also called overlays, or when allowing user self-registration.")

[RP-Initiated Logout \(Specification from OpenID Foundation\)](https://openid.net/specs/openid-connect-rpinitiated-1_0.html "Specification from OpenID Foundation")

[Single Logout Flows](../Development/single-logout-flows-0584b5f.md "It's good practice to encourage users of your applications to log out at the end of their session. If malicious users can access user sessions, either by gaining access to artifacts such as cookies or by finding unattended clients, malicious users can impersonate the rightful owners of the sessions.")

