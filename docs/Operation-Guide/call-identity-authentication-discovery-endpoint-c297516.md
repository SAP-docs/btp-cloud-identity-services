<!-- loioc297516bae4547eb82eeed80fea2b937 -->

# Call Identity Authentication Discovery Endpoint

This document explains how to call the discovery endpoint.



OpenID Connect Discovery enables clients to verify the identity of the end user based on the authentication performed by Identity Authentication.



## **Call Discovery Endpoint**

**URI:**`https://<tenant ID>.accounts.ondemand.com/.well-known/openid-configuration`

**HTTP Method:***GET*



### Request Examples

```
https://my-tenant.ondemand.com/.well-known/openid-configuration
```



## **Result**



### Result

```
	
{
  "issuer" : "https://my-tenant.ondemand.com",
  "authorization_endpoint" : "https://my-tenant.ondemand.com/oauth2/authorize",
  "token_endpoint" : "https://my-tenant.ondemand.com/oauth2/token",
  "userinfo_endpoint" : "https://my-tenant.ondemand.com/oauth2/userinfo",
  "end_session_endpoint" : "https://my-tenant.ondemand.com/oauth2/logout",
  "jwks_uri" : "https://my-tenant.ondemand.com/oauth2/certs",
  "introspection_endpoint":"https://my-tenant.ondemand.com/oauth2/introspect",
  "revocation_endpoint":"https://my-tenant.ondemand.com/oauth2/revoke",
  "response_types_supported" : [ "code", "id_token", "token" ],
  "grant_types_supported" : [ "password", "authorization_code", "refresh_token", "client_credentials", "urn:ietf:params:oauth:grant-type:jwt-bearer", "urn:ietf:params:oauth:grant-type:token-exchange"],
  "subject_types_supported" : [ "public" ],
  "id_token_signing_alg_values_supported" : [ "RS256" ],
  "scopes_supported" : [ "openid", "email", "profile", "offline_access" ],
  "token_endpoint_auth_methods_supported" : [ "tls_client_auth", "client_secret_basic", "client_secret_post", "private_key_jwt" ],
  "claims_supported" : [ "sub", "iss", "exp", "iat", "nonce", "email", "email_verified", "given_name", "family_name", "zone_uuid", "user_uuid", "preferred_username", "name", "sid"],
  "code_challenge_methods_supported" : [ "plain", "S256" ],
  "tls_client_certificate_bound_access_tokens" : true,
  "frontchannel_logout_supported" : true,
  "frontchannel_logout_session_supported" : true
}
```

 

> ### Note:  
> The format of the `issuer` depends on the configuration in the administration console for SAP Cloud Identity Services. For more information, see [Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md).

> ### Remember:  
> IAS supports only the assertion created by security token service \(STS\) model. For more information, see [OAuth Assertion Framework](https://datatracker.ietf.org/doc/html/rfc7521#section-3).

**Related Information**  


[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

[Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services.")

[OpenID Connect Discovery 1.0 incorporating errata set 1](https://openid.net/specs/openid-connect-discovery-1_0.html)

