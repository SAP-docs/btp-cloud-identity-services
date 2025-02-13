<!-- loiof85344d607e0473d815f5745cd91d00a -->

# Configure PKCE for Corporate Identity Providers

If your corporate identity provider supports Proof Key for Code Exchange \(PKCE\) and you have public applications that aren't capable of keeping client secrets, such as mobile applications, native applications, and single page applications, we recommend enabling this feature.



## Context

Proof Key for Code Exchange \(PKCE\) is an enhancement of the authorization code flow to mitigate the threat of malicious actors from intercepting the authorization code.

> ### Note:  
> We only support the code challenge method S256.

For more information, see [RFC7636](https://datatracker.ietf.org/doc/html/rfc7636).



## Procedure

1.  In the administration console for SAP Cloud Identity Services, navigate to the OpenID Connect configuration of your corporate identity provider.

    For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).

2.  Enable the *Enable PKCE \(S256\)* check box.

    Use the *Validate* button to confirm that the configuration is still working.

3.  Save your entries.


**Related Information**  


[Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow with PKCE](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-a721157.md "The authorization code flow with PKCE is recommended for public clients that aren’t capable of keeping the client secrets.")

