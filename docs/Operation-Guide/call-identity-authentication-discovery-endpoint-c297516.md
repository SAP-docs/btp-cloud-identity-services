<!-- loioc297516bae4547eb82eeed80fea2b937 -->

# Call Identity Authentication Discovery Endpoint

This document explains how to call the discovery endpoint.



OpenID Connect Discovery enables clients to verify the identity of the end user based on the authentication performed by Identity Authentication.



## **Call Discovery Endpoint**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/.well-known/openid-configuration</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

**HTTP Method:***GET*



### Request Parameters


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Required

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
<th valign="top">

Parameter Type

</th>
</tr>
<tr>
<td valign="top">

`appid`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Used to identify the corresponding Identity Authentication application.

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`app_tid`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Reserved.

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`client_id`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Used to identify the corresponding client of the Identity Authentication application.

</td>
<td valign="top">

Request body

</td>
</tr>
</table>



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
  "claims_supported" : [ "iss", "ias_iss", "iat", "exp", "auth_time", "sid", "jti", "nonce", "sub", "email", "email_verified", "given_name",
        "middle_name", "family_name", "preferred_username", "name", "scim_id", "groups", "aud", "azp", "app_tid", "ias_apis", "at_hash",
        "sap_id_type", "sap_gtid"],
  "code_challenge_methods_supported" : [ "plain", "S256" ],
  "tls_client_certificate_bound_access_tokens" : true,
  "frontchannel_logout_supported" : true,
  "frontchannel_logout_session_supported" : true,
  "backchannel_logout_supported": true,
  "backchannel_logout_session_supported": true,
  "authorization_response_iss_parameter_supported": true
}
```

> ### Note:  
> The format of the `issuer` depends on the configuration in the administration console for SAP Cloud Identity Services. For more information, see [Tenant OpenID Connect \(OIDC\) Configurations](tenant-openid-connect-oidc-configurations-3d6abcc.md).

> ### Restriction:  
> -   If the `issuer` doesn't use HTTPS, then this tenant isn't OIDC-compliant. Not using HTTPS can cause integration failures. Changing the protocol at the tenant level can also cause integration failures. You can change the protocol at the application level to make the issuer OIDC compliant for that application. In the *OpenID Connect Configuration* of the application, set *Enforce Compliant OIDC Issuer*.
> 
> -   If *Enforce Compliant OIDC Issuer* is enabled, you must provide one of the following parameter combinations in your discovery endpoint request:
> 
>     -   `client_id` and optional `app_tid`
> 
>     -   `appid`
> 
> 
>     Without one of these parameter combinations, the discovery endpoint returns an issuer URL without the protocol, which causes OIDC validation to fail.

> ### Remember:  
> Identity Authentication supports only the assertion created by the security token service \(STS\) model. For more information, see [OAuth Assertion Framework](https://datatracker.ietf.org/doc/html/rfc7521#section-3).

**Related Information**  


[Configuring OpenID Connect \(OIDC\)](configuring-openid-connect-oidc-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect (OIDC) protected applications.")

[Configure OpenID Connect \(OIDC\) Application](configure-openid-connect-oidc-application-8a0aa2e.md "This document is intended to help you configure an OpenID Connect (OIDC) application in the administration console for SAP Cloud Identity Services.")

[OpenID Connect Discovery 1.0 incorporating errata set 1](https://openid.net/specs/openid-connect-discovery-1_0.html)

