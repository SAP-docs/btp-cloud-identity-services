<!-- loio632df37fb9e2463393715ec1facf39bf -->

# Configure the Client to Call Identity Authentication Token Exchange

With the Token Exchange flow you can exchange one token for another. For more information, see [OAuth 2.0 Token Exchange](https://datatracker.ietf.org/doc/html/rfc8693).



## **Request**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/token</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).

**Content-Type**`application/x-www-form-urlencoded`

**HTTP Method:***POST*



### Request Headers


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Required

</th>
<th valign="top">

Values

</th>
</tr>
<tr>
<td valign="top">

`Content-Type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

application/x-www-form-urlencoded

</td>
</tr>
<tr>
<td valign="top">

`Authorization`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

-   `Basic` Username and password are:

    Client ID and a Secret to authenticate the client \(relying party\). For more information, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

    > ### Note:  
    > The client ID and secret must be encoded using the "application/x-www-form-urlencoded" encoding algorithm.

-   X.509 Certificate
-   JWT \(client\_assertion\)



</td>
</tr>
</table>



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

Additional Information

</th>
<th valign="top">

Parameter Type

</th>
</tr>
<tr>
<td valign="top">

`grant_type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

`urn:ietf:params:oauth:grant-type:token-exchange`

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

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The user ID configured for basic authentication for the application. For more information, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`client_secret`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

The client secret configured for basic authentication for the application. For more information, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`subject_token`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

A security token that represents the identity of the party on behalf of whom the request is being made, as stated in the OAuth 2.0 Token Exchange specification.

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`subject_token_type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The type of the security token in the `subject_token`.

Allowed values:

-   `urn:sap:identity:oauth:token-type:saml2-session`
-   `urn:ietf:params:oauth:token-type:access_token`
-   `urn:ietf:params:oauth:token-type:refresh_token`
-   `urn:ietf:params:oauth:token-type:id_token`
-   `urn:ietf:params:oauth:token-type:jwt`

    > ### Tip:  
    > You can use either a JWT-based access token or an id\_token.
    > 
    > If you want to exchange a JWT token of a corporate identity provider \(IdP\), you should do it before an exchange with a JWT bearer token.




</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`requested_token_type`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

The type of the requested security token.

Allowed values for `requested_token_type` parameter:

-   `urn:ietf:params:oauth:token-type:access_token`
-   `urn:ietf:params:oauth:token-type:id_token`
-   `urn:ietf:params:oauth:token-type:saml2`
-   `urn:sap:identity:oauth:token-type:saml2-header`

> ### Note:  
> The exchange of an OpenID Connect token with SAML 2.0 is possible in two scenarios, depending on the requested token type string:
> 
> -   `urn:sap:identity:oauth:token-type:saml2-header` - [2043039](https://me.sap.com/notes/2043039) 
> -   `urn:ietf:params:oauth:token-type:saml2` - [SAML 2.0 Bearer Assertion Flow for OAuth 2.0 Client](https://help.sap.com/docs/SAP_NETWEAVER_750/e815bb97839a4d83be6c4fca48ee5777/01043cc6765b48cfbc1564a9839a29ee.html)



</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`resource`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Use provided API names. For more information, see [Consuming APIs from Other Applications](../Development/consuming-apis-from-other-applications-29e204d.md).

> ### Note:  
> If `resource` parameter is used to consume APIs from other applications, then the returned token is always of type `urn:ietf:params:oauth:token-type:access_token` even if `requested_token_type` is requested for type `id_token`.



</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`refresh_expiry`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Reduces the expiry of a refresh token. It is useful if your application is called from mobile and web applications, and both have different session requirements. If you set the token lifetime to 0 or less, you won't receive a `refresh_token` in response.

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`token_format`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

The `token_format` can be set to `opaque` to retrieve an opaque access token or to `jwt` to retrieve a JWT-based access token. If not set, the current defaults per grant type are used.

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

`scope`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

Value must be space deliminated parameter, for example: `scope=openid email`.

The supported values are:

-   `openid`
-   `email`
-   `profile`
-   `groups`
-   `offline_access`

    > ### Note:  
    > The new tokens are independently created from the Identity Authentication Web session. This means that even if a user logs out from Identity Authentication the `refresh_token` will exist in the database until it expires, and can be used to perform the refresh token flow if the user is not present in Identity Authentication with a Web session.




</td>
<td valign="top">

Request body

</td>
</tr>
</table>



## **Examples**



> ### Example:  
> *Request*
> 
> ```
> 
> POST /oauth2/token
> Content-Type: application/x-www-form-urlencoded
> 
> grant_type=urn:ietf:params:oauth:grant-type:token-exchange&
> client_id=a90ca226sbc34-soc5-dcf6-6k8a6b9f2469&
> client_secret=OWSu0/0sSUeUCG1LAYmSQ10Ut0yrfPz&
> subject_token=Zjk1YTI3YERzNGZlZmTlNzZjNzk4YTY2ZjdlZjYwMacw&
> subject_token_type=urn:ietf:params:oauth:token-type:access_token&
> scope=openid
> ```
> 
> *Response*
> 
> ```
> 
> Content-Type: application/json
>  
> {
>     "access_token": "dzEyYTM0YmM2OWZhZnU3NmE3OThzNjZmN3NmNjg3MQ",
>     "refresh_token": "s95s27af4fefae76c798a66f7ef9034",
> 	"issued_token_type": "urn:ietf:params:oauth:token-type:access_token",
>     "id_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ey
> JzdWIiOiJQMTIzNDU2IiwiYXVkIjoiMjAzZjYyMDktMjRmZi00MmY1LW
> E0MTMtNmRlNWE5M2ZjMjYxIiwidXNlcl91dWlkIjoiMDEyM2E0NS1mMW
> FmLTFmMWMtYTMxMy03NDZkMTIwYWJjZDkiLCJtYWlsIjoiZG9uYS5tb2
> 9yZUBleGFtcGxlLmNvbSIsImlzcyI6Imh0dHBzOi8vdGVzdHRlbmFudC
> 50ZXN0LmNvbSIsImxhc3RfbmFtZSI6Ik1vb3JlIiwiZXhwIjoxNjM5MT
> Q0MDEwLCJpYXQiOjE2MzkxNDA0MTAsImZpcnN0X25hbWUiOiJEb25hIi
> wianRpIjoiMzFlMzJjNWYtNjljcC00NmE2LWE5MDctOTExZDExMjA1cz
> BzIn0.QYftNy7WgISWoKpRXh4_RX5UDNXsXDTndYuIA85L2II",
>     "token_type": "Bearer",
>     "expires_in": 3600
> }
> ```

> ### Example:  
> *Request*
> 
> ```
> 
> https://my-tenant.ondemand.com/oauth2/token?grant_type=urn:ietf:params:oauth:grant-type:token-exchange&
> client_id=a90ca226sbc34-soc5-dcf6-6k8a6b9f2469&
> client_secret=OWSu0/0sSUeUCG1LAYmSQ10Ut0yrfPz&
> subject_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJQMTIzNDU2IiwiYXVkIjoiMjAzZjYyMDktMjRmZi00MmY1LWE0MTMtNmRlNWE5M2ZjMjYxIiwidXNlcl91dWlkIjoiMDEyM2E0NS1mMWFmLTFmMWMtYTMxMy03NDZkMTIwYWJjZDkiLCJtYWlsIjoiZG9uYS5tb29yZUBleGFtcGxlLmNvbSIsImlzcyI6Imh0dHBzOi8vdGVzdHRlbmFudC50ZXN0LmNvbSIsImxhc3RfbmFtZSI6Ik1vb3JlIiwiZXhwIjoxNjM5MTQ0MDEwLCJpYXQiOjE2MzkxNDA0MTAsImZpcnN0X25hbWUiOiJEb25hIiwianRpIjoiMzFlMzJjNWYtNjljcC00NmE2LWE5MDctOTExZDExMjA1czBzIn0.QYftNy7WgISWoKpRXh4_RX5UDNXsXDTndYuIA85L2II&
> subject_token_type=urn:ietf:params:oauth:token-type:id_token&
> requested_token_type=urn:ietf:params:oauth:token-type:saml2&
> resource=urn:sap:identity:application:provider:name:SAML2SSO
> ```
> 
> *Response*
> 
> ```
> 
> Content-Type: application/json
> 
> {
> "access_token": "<Base64Url-Encoded-SAML2-Bearer-Assertion>",
> "issued_token_type": "urn:ietf:params:oauth:token-type:saml2",
> "token_type": "Bearer",
> "expires_in": 900
> }
> ```

**Related Information**  


[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

[JSON Web Token \(JWT\) Profile for OAuth 2.0 Client Authentication and Authorization Grants](https://datatracker.ietf.org/doc/html/rfc7523)

