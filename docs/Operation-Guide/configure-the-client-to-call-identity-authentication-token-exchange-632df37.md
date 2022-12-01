<!-- loio632df37fb9e2463393715ec1facf39bf -->

# Configure the Client to Call Identity Authentication Token Exchange

With the Token Exchange flow you can exchange one token for another. For more information, see [OAuth 2.0 Token Exchange](https://datatracker.ietf.org/doc/html/rfc8693).





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

`urn:ietf:params:oauth:grant-type:token-exchange`



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

`subject_token`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

String



</td>
<td valign="top">

A security token that represents the identity of the party on behalf of whom the request is being made, as stated in the OAuth 2.0 Token Exchange specification.



</td>
<td valign="top">

Path



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

String



</td>
<td valign="top">

The type of the security token in the `subject_token`. Supported types:

-   `SAML2 Session Index`
-   `OAuth2 Access Token`



</td>
<td valign="top">

Request body



</td>
</tr>
</table>



### Request Example

```

https://my-tenant.ondemand.com/oauth2/token?grant_type=urn:ietf:params:oauth:grant-type:token-exchange&
client_id=a90ca226sbc34-soc5-dcf6-6k8a6b9f2469&
client_secret=OWSu0/0sSUeUCG1LAYmSQ10Ut0yrfPz&
subject_token=Zjk1YTI3YERzNGZlZmTlNzZjNzk4YTY2ZjdlZjYwMacw
subject_token_type=urn:ietf:params:oauth:token-type:access_token
```



## **Response**



### Response Example

```

Content-Type: application/json
 
{
    "access_token": "dzEyYTM0YmM2OWZhZnU3NmE3OThzNjZmN3NmNjg3MQ",
    "refresh_token": "s95s27af4fefae76c798a66f7ef9034",
	"issued_token_type": "urn:ietf:params:oauth:token-type:access_token",
    "id_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ey
JzdWIiOiJQMTIzNDU2IiwiYXVkIjoiMjAzZjYyMDktMjRmZi00MmY1LW
E0MTMtNmRlNWE5M2ZjMjYxIiwidXNlcl91dWlkIjoiMDEyM2E0NS1mMW
FmLTFmMWMtYTMxMy03NDZkMTIwYWJjZDkiLCJtYWlsIjoiZG9uYS5tb2
9yZUBleGFtcGxlLmNvbSIsImlzcyI6Imh0dHBzOi8vdGVzdHRlbmFudC
50ZXN0LmNvbSIsImxhc3RfbmFtZSI6Ik1vb3JlIiwiZXhwIjoxNjM5MT
Q0MDEwLCJpYXQiOjE2MzkxNDA0MTAsImZpcnN0X25hbWUiOiJEb25hIi
wianRpIjoiMzFlMzJjNWYtNjljcC00NmE2LWE5MDctOTExZDExMjA1cz
BzIn0.QYftNy7WgISWoKpRXh4_RX5UDNXsXDTndYuIA85L2II",
    "token_type": "Bearer",
    "expires_in": 3600
}
```

 

**Related Information**  


[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

[JSON Web Token \(JWT\) Profile for OAuth 2.0 Client Authentication and Authorization Grants](https://datatracker.ietf.org/doc/html/rfc7523)

