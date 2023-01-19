<!-- loio01a0440acd1648189644a2ff60f3772f -->

# Configure the Client to Call Identity Authentication JWT Bearer Token

With the JWT bearer flow you can use an `id_token` ID from an application which is in the same Identity Authentication tenant, or an external `id_token` whose issuer is trusted by Identity Authentication.



> ### Note:  
> The issuer of the external corporate identity provider must be configured as a corporate identity provider and set as a default identity provider or configured via Authentication Rules \(Conditional Authentication\) in the administration console for SAP Cloud Identity Services.



## **Request**

**URI:**`https://<tenant ID>.accounts.ondemand.com/oauth2/token`

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

`Authentication`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

-   Basic Authentication -

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

`urn:ietf:params:oauth:grant-type:jwt-bearer`



</td>
<td valign="top">

Path



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

Path



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

Path



</td>
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

**Same tenant ID token:**

-   user identifier:

    -   if "`user_uuid`" claim is provided, it will be used to search the user by user\_uuid

    -   otherwise "`sub`" claim will be used, therefore the subject name identifier from the other application will be checked to accordingly search the user in the tenant


-   audience: must contain the client ID of the requested application in "`aud`" claim


**External ID token:**

-   user identifier: according to the Subject Name Identifier configuration of the used corporate identity provider, the value of "email" or "sub" claim will be used to search the user by e-mail

-   audience: must contain requested Identity Authentication issuer in "`aud`" claim




</td>
<td valign="top">

Path



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

String



</td>
<td valign="top">

Reduces the expiration of a refresh token. It is useful if your application is called from mobile and web applications, and both have different session requirements. If you set the token lifetime to 0, you won't receive a `refresh_token` in response.



</td>
<td valign="top">

Path



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

String



</td>
<td valign="top">

The `token_format` can be set to `opaque` to retrieve an opaque access token or to `jwt` to retrieve a JWT based access token. If not set, the current defaults per grant type are used.



</td>
<td valign="top">

Request body



</td>
</tr>
</table>



### Request Example

```

https://my-tenant.ondemand.com/oauth2/token?grant_type=urn:ietf:params:oauth:grant-type:jwt-bearer&
client_id=c95ad226-fg34-abc6-abc6-6e8a6b9f2442&
client_secret=PASu9/0sTUeUCG1LAYmSQ18Ut0zrfMz&
assertion=eyJraWQiOiJva3JFVVNsbHRIbGlL...hoXvzy2TgmdPS0LlAXA
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

 

**Related Information**  


[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

[JSON Web Token \(JWT\) Profile for OAuth 2.0 Client Authentication and Authorization Grants](https://datatracker.ietf.org/doc/html/rfc7523)

