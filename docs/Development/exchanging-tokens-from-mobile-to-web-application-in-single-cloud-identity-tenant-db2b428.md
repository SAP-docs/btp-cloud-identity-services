<!-- loiodb2b4288e28746d59a950e96b49cf441 -->

# Exchanging Tokens from Mobile to Web Application in Single Cloud Identity Tenant

Configure token exchange from mobile to web application or within different parts of the same application when using a single SAP Cloud Identity Services tenant.

In the token exchange process, an application requests and obtains a token \(such as a JWT token\) from an identity provider and then exchanges these tokens with another application or within different parts \(microservices\) of the same application. This way users do not need to re-authenticate when accessing different applications.



<a name="loiodb2b4288e28746d59a950e96b49cf441__section_w1c_mtv_fcc"/>

## Example Process Overview

The following process outlines how tokens are exchanged from mobile to web application, resulting in user authentication using Identity Authentication as the identity provider.

1.  Obtain an opaque token.

    The mobile app sends a request to Identity Authentication using a long-lived refresh token to obtain an opaque access token from the service. The mobile app sends the request to the`/token` endpoint.

2.  Pass the opaque token to the web application.

    The mobile app opens a web browser and navigates to the URL of the web application. It includes the opaque token as part of the URL so the web application can use it.

3.  Validate the opaque token and create a session.

    The web application receives the opaque token and sends the opaque token with its own client credentials to Identity Authentication to validate it and retrieve user information. The web app gets the user details in exchange for the opaque token and its client credentials, and creates a session. The web app uses the `/introspect` endpoint to perform the token validation and user information retrieval.


In the case of internal application token exchange, different microservices within the same application might need to share tokens to facilitate the communication. For example, after authenticating, the main application service may request an access token and then pass it to a microservice that handles specific functionalities.



<a name="loiodb2b4288e28746d59a950e96b49cf441__section_icl_mtv_fcc"/>

## Call the Token Endpoint

For more information, see [Configure the Client to Call Identity Authentication Token Exchange](../Operation-Guide/configure-the-client-to-call-identity-authentication-token-exchange-632df37.md)



<a name="loiodb2b4288e28746d59a950e96b49cf441__section_iqp_qmw_fcc"/>

## Call the Introspect Token Endpoint

For more information, see [Call Identity Authentication Introspect Token Endpoint](../Operation-Guide/call-identity-authentication-introspect-token-endpoint-a05f14c.md) 

