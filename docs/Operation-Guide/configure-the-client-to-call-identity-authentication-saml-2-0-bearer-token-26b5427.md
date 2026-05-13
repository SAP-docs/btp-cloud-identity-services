<!-- loio26b5427ecce1425da78fdd4381328483 -->

# Configure the Client to Call Identity Authentication SAML 2.0 Bearer Token

In the SAML 2.0 Bearer Token flow, you exchange one token for another. For more information, see [RFC 7522](https://datatracker.ietf.org/doc/html/rfc7522).



## Prerequisites

-   For your business application, there’s an OpenID Connect \(OIDC\) application in Identity Authentication.

    For more information, see [Create OpenID Connect \(OIDC\) Application](create-openid-connect-oidc-application-62fb1c3.md).

-   For your OpenID Connect \(OIDC\) application in Identity Authentication, you've prepared an authentication credential for the API call. The API supports the following authentication schemes:

    -   Basic

        For more information, see `Authorization` in the *Request Header* table below.

    -   X.509

        For more information, see `Authorization` in the *Request Header* table below.

    -   JWT \(client\_assertion\)

        -   Trust by issuer: You must include the `client_id` in the request.

        -   Trust by URI: Including `client_id` in the request is optional.


        For more information, see the *Request Parameters* table below.


    For more information, see [API Authentication](api-authentication-9d200d5.md).




## Request

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/token</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

**Content-Type** `application/x-www-form-urlencoded`

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

`assertion`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

Enter a Base64URL-encoded SAML assertion.

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

Enter the identifier for the Identity Authentication application.

> ### Note:  
> This parameter is optional if the request uses authentication.



</td>
<td valign="top">

Request body

</td>
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

`urn:ietf:params:oauth:grant-type:saml2-bearer`

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

The parameter is reserved.

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

Enter the client secret for basic authentication. For more information, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`max_exchange_period`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Set a limit for how long the application can exchange user tokens without re-authenticating after the initial token is acquired. You select a numeric value between one hour and 4320 hours \(six months\).

> ### Remember:  
> If the `max_exchange_period` value is smaller than the configuration in token policy, the value overrides the token policy configuration and applies when the token is exchanged or refreshed. If the value is larger, the system ignores it and uses the existing token policy configuration. For more information, see [Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md).



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

Reduces the expiration of a refresh token. It's useful if your application is called from mobile and web applications, and both have different session requirements. If you set the token lifetime to 0, you won't receive a `refresh_token` in response.

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

Enter the Uniform Resource Name \(URN\) for the dependency used by the application.

For more information, see [Consuming APIs from Other Applications](../Development/consuming-apis-from-other-applications-29e204d.md).

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

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Parameter values must be space-delimited. For example: `scope=openid email`.

Supported values:

-   `openid`
-   `email`
-   `profile`
-   `groups`
-   `offline_access`

    > ### Note:  
    > Tokens are created independently from the Identity Authentication web session. Even if a user logs out from Identity Authentication, the `refresh_token` remains in the database until it expires. You can use it for the refresh token flow if the user doesn't have an active session in Identity Authentication.




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

You can set `token_format` to `opaque` to retrieve an opaque access token, or to `jwt` to retrieve a JWT-based access token. If you don't set the parameter, the system uses the current defaults for each grant type.

</td>
<td valign="top">

Request body

</td>
</tr>
</table>



### Request Example

```

POST /oauth2/token
Content-Type: application/x-www-form-urlencoded

grant_type=urn:ietf:params:oauth:grant-type:saml2-bearer&
client_id=c95ad226-fg34-abc6-abc6-6e8a6b9f2442&
client_secret=PASu9/0sTUeUCG1LAYmSQ18Ut0zrfMz&
assertion=PHNhbWw6QXNzZXJ0aW9uIElEPSJB...1sOkFzc2VydGlvbj4=
```



## **Response**



### Response Example

```

Content-Type: application/json
 
{
    "access_token": "dzEyYTM0YmM2OWZhZnU3NmE3OThzNjZmN3NmNjg3MQ",
    "refresh_token": "s95s27af4fefae76c798a66f7ef9034",
    "id_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJQMT
	IzNDU2IiwiYXVkIjoiMjAzZjYyMDktMjRmZi00MmY1LWE0MTMtNmRlNWE5M2ZjM
	jYxIiwidXNlcl91dWlkIjoiMDEyM2E0NS1mMWFmLTFmMWMtYTMxMy03NDZkMTIw
	YWJjZDkiLCJtYWlsIjoiZG9uYS5tb29yZUBleGFtcGxlLmNvbSIsImlzcyI6Imh
	0dHBzOi8vdGVzdHRlbmFudC50ZXN0LmNvbSIsImxhc3RfbmFtZSI6Ik1vb3JlIi
	wiZXhwIjoxNjM5MTQ0MDEwLCJpYXQiOjE2MzkxNDA0MTAsImZpcnN0X25hbWUiO
	iJEb25hIiwianRpIjoiMzFlMzJjNWYtNjljcC00NmE2LWE5MDctOTExZDExMjA1
	czBzIn0.QYftNy7WgISWoKpRXh4_RX5UDNXsXDTndYuIA85L2II",
    "token_type": "Bearer",
    "expires_in": 3600
}
```

