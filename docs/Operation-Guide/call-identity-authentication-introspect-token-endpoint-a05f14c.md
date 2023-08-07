<!-- loioa05f14caeb5c403e99a7020d2bf58617 -->

# Call Identity Authentication Introspect Token Endpoint

The introspect token endpoint is an option for clients to get long expiring refresh tokens, opaque access and id tokens in JWT format validated.



The token recation endpoint is implemented according to [RFC 7662 OAuth 2.0 Token Introspection](https://www.rfc-editor.org/rfc/rfc7662).



## **Request**

**URI:**`https://<tenant ID>.accounts.ondemand.com/oauth2/introspect`

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

-   POST
-   X.509 Certificate
-   Bearer <client\_credential\_token\>\)



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

Description



</th>
<th valign="top">

Parameter Type



</th>
</tr>
<tr>
<td valign="top">

`token`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

Must contain the JWT or opaque token from the issuer.



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`token_type_hint`



</td>
<td valign="top">

No



</td>
<td valign="top">

string



</td>
<td valign="top">

 



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

No



</td>
<td valign="top">

string



</td>
<td valign="top">

Used to identify the corresponding Identity Authentication application.

> ### Note:  
> The `client_id` parameter is mandatory if the request is provided without authentication.



</td>
<td valign="top">

Request body



</td>
</tr>
</table>



### Request Example

```
token=0ab82505123c12ffe7c4e9a2b0158cn7
```



## **Response**



### Response Example

*If token is valid:*

```

Content-Type: application/json

{
 "active": true,
 "aud": "a123456e-314a-4923-899c-05c535c3d7f9",
 "username": "P12345",
 "sub": "P12345",
 "user_uuid": "158a1b2c7-981az-69ab9-8079-d824da69c681",
 "mail": "dona.moore@example.com",
 "iss": "https://my-_tenant.accounts.ondemand.com",
 "last_name": "Moore",
 "exp": 1588019044,
 "iat": 158801376,
 "first_name": "Dona",
 "jti": "38e42330-de7a-4130-a3a1-b582b528da98"
}
```

*If token is not valid/expired/not known or any other token related issue:*

```

Content-Type: application/json

{
 "active": false
}
```



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code



</th>
<th valign="top">

Reason



</th>
</tr>
<tr>
<td valign="top">

200 OK



</td>
<td valign="top">

Successful operation.



</td>
</tr>
<tr>
<td valign="top">

401 Unauthorized



</td>
<td valign="top">

The client is not authenticated.



</td>
</tr>
</table>



