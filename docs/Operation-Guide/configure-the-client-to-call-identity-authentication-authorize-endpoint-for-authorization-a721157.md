<!-- loioa721157cd40544eb9bad40085cf8ec15 -->

# Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow with PKCE

The authorization code flow with PKCE is recommended for public clients that aren’t capable of keeping the client secrets.



<a name="loioa721157cd40544eb9bad40085cf8ec15__section_j53_1s1_dpb"/>

## Prerequisites

-   For your business application, there’s an OIDC application in Identity Authentication.

    For more information, see [Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md).

-   For your OIDC application in Identity Authentication, you've prepared an authentication credential for the API call. The API supports the following authentication schemes:

    -   Basic

        For more information, see `Authorization` in [Request Header](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md#loio94ff0b4b0baa45a893c7cd24254b72b7__request_header_table) table below.

    -   X.509

        For more information, see `Authorization` in [Request Header](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md#loio94ff0b4b0baa45a893c7cd24254b72b7__request_header_table) table below.

    -   JWT \(client\_assertion\)

        -   Trust by issuer: You must include the `client_id` in the request.

        -   Trust by URI: Including `client_id` in the request is optional.


        For more information, see [Request Parameters](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md#loio94ff0b4b0baa45a893c7cd24254b72b7__request_parameter_table) table below.


    For more information, see [API Authentication](api-authentication-9d200d5.md).




This document explains how to call the `authorize` endpoint and what are the authorize request parameters supported by Identity Authentication for the authorization code flow with PKCE.

> ### Note:  
> Public clients are applications that aren’t capable of keeping the client secret, such as mobile applications, native applications, and single page applications.



## **Request**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/authorize</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

**HTTP Method:***GET*



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

`client_id`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

Used to identify the corresponding Identity Authentication application.

> ### Note:  
> The `client_id` parameter is optional if the request is provided with authentication.



</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

`code_challenge`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

Client created code.

> ### Tip:  
> You can use online PKCE generator tools to generate the `code_challenge` values.



</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

`code_challenge_method`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

Code verifier transformation method is "S256" or "plain".

</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

`redirect_uri`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

-   [Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md)
-   [Redirect URIs, Post Logout Redirect URI Rules](redirect-uris-post-logout-redirect-uri-rules-48fdb9a.md)



</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

`response_type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The supported value is `code`.

</td>
<td valign="top">

Query

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

Query

</td>
</tr>
<tr>
<td valign="top">

`state`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

Free text.

</td>
<td valign="top">

Query

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

Query

</td>
</tr>
<tr>
<td valign="top">

`login_hint`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

The `login_hint` parameter helps the user when he or she is known to the service provider \(SP\). Thus it prevents the user from re-typing the user identifier on the logon or conditional screen.

Supported values are the allowed logon identifiers for the users. The options are *User ID*, *Login Name*, and *Email* \(For SAML 2.0\). For more information, see [Configure Allowed Logon Identifiers](configure-allowed-logon-identifiers-3adf1ff.md) .

</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

`logout_uri`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

-   [Configure OpenID Connect Application for Authorization Code Flow](configure-openid-connect-application-for-authorization-code-flow-4a94254.md)
-   [Logout URI Rules](logout-uri-rules-789c752.md)



</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

`max_age`

</td>
<td valign="top">

No

</td>
<td valign="top">

integer

</td>
<td valign="top">

Maximum time in seconds since the user was last authenticated. When `max_age` has been reached, the user must re-authenticate.

</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

`nonce`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Free text.

</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

`prompt`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

This parameter enables the client to determine if the user is still present in the current session.

Supported values are:

-   *login*

    Force reauthentication of the user.

-   *none*

    Without user interaction, check if there is an exisiting user session. If there is a session, continue as normal. If there is no session or if the user is forced to authenticate for other reasons, return the error code ***login\_required***.




</td>
<td valign="top">

Query

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

Reduces the expiration of a refresh token. It's useful if your application is called from mobile and web applications, and both have different session requirements. If you set the token lifetime to 0, you won't receive a `refresh_token` in response.

</td>
<td valign="top">

Query

</td>
</tr>
</table>



### Request Example



### Request Example \(`code_challenge` and `code_challenge_method` are required\)

```
https://my-tenant.ondemand.com/oauth2/authorize?response_type=code&scope=openid&client_id=94ff0b4b0baa45a893c7cd24254b72b7&state=state&redirect_uri=https://example.com&code_challenge=MCVg2_O79Qpr6E7HDA0ik5R-ylwjT-_H3oUgdDQ9W50&code_challenge_method=S256
```



## **Response**



### Response Headers


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`code`

</td>
<td valign="top">

The `code` is generated by Identity Authentication and is returned in the URL as a parameter. It must be used when calling the token endpoint.

> ### Note:  
> The parameter can be used within two minutes after it is generated and returned in the URL. It can be used only once.



</td>
</tr>
</table>



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code

</th>
<th valign="top">

Reason

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

302 Found

</td>
<td valign="top">

Successful operation.

</td>
<td valign="top">

Additionally provides a URL in the header field Location.

> ### Note:  
> The URL contains `code` necessary for the token endpoint.



</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

Missing or wrong parameter

</td>
<td valign="top">

 

</td>
</tr>
</table>



### Response Example

```
Location:
 https://www.example.com/?code=4454554df477w01s34540672dc462e6f0&state=state
```



**Related Information**  


[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

[Proof Key for Code Exchange by OAuth Public Clients \(IETF\)](https://tools.ietf.org/html/rfc7636)

