<!-- loio52b93b08f4654e659a9abf93ca86d902 -->

# Configure the Client to Call Identity Authentication Token Endpoint for Client Credentials Flow

The token endpoint is used to get the user's access token.



This document explains how to call the token endpoint and what are the parameters supported by Identity Authentication.



## **Request**

**URI:**`https://<tenant ID>.accounts.ondemand.com/oauth2/token`

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

Description



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

client\_credentials



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
grant_type=client_credentials&client_id=12b52d2c-1q34-5r5t-a576-75e85asdf523
```



## **Response**



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

200 OK



</td>
<td valign="top">

Successful operation.



</td>
<td valign="top">

Returns `access_token`.



</td>
</tr>
<tr>
<td valign="top">

400 Bad Request



</td>
<td valign="top">

Missing or wrong parameter.



</td>
<td valign="top">

Returns an information about the error.



</td>
</tr>
</table>



### Response Payload Example

```

{
  "access_token":
"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIxMnM1NHc2YS0xdzU
2LTVlOGItZjI1Ni0wN3YwNXZmZ2IzMTIiLCJzdWIiOiIxMnM1NHc2YS0xdzU2LTVl
OGItZjI1Ni0wN3YwNXZmZ2IzMTIiLCJpc3MiOiJodHRwczovLzx0ZW5hbnQgSUQ-L
mFjY291bnRzLm9uZGVtYW5kLmNvbSIsImV4cCI6MTU4ODAyNzk3MCwiaWF0IjoxNT
g4MDI0MTEyLCJqdGkiOiIzMDhiYTg5NC0zMGE0LTQ4MDUtYWUzOS1vc2EyYXNkMjU
2ZTIifQ.9IJLkgsKQtYzMRrHUY004X7OJYWI-L8QV1oG42EZ0Kc",
  "token_type": "Bearer",
  "expires_in": 3600
}
}
```

> ### Note:  
> The format of the `issuer` depends on the configuration in the administration console for SAP Cloud Identity Services. For more information, see [Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md).



**Related Information**  


[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

