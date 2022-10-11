<!-- loio1ca3dc0ed2f0463380c86355a52c47b9 -->

# Configure the Client to Call Identity Authentication Authorize Endpoint for Implicit Flow

The authorize endpoint is used for authentication and returns the `id_token` when using the implicit flow.



This document explains how to call the authorize endpoint and what are the request parameters supported by Identity Authentication for the implicit flow.



## **Request**

**URI:**`https://<tenant ID>.accounts.ondemand.com/oauth2/authorize`

` `

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

redirect\_uri



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

One of the valid URIs configured for the application. You can configure up to five URIs. For more information, see [Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md).



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

response\_type



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

The supported value is `id_token`



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

scope



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

The supported value is `openid`



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

client\_id



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

state



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

Path



</td>
</tr>
<tr>
<td valign="top">

nonce



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

Path



</td>
</tr>
<tr>
<td valign="top">

login\_hint



</td>
<td valign="top">

No



</td>
<td valign="top">

string



</td>
<td valign="top">

The `login_hint` parameter facilitates the user when he or she is known to the service provider \(SP\). Thus it prevents the user from re-typing the user identifier on the logon or conditional screen.

Supported values are the allowed logon identifiers for the users. The options are *\(For SAML 2.0User ID*, *Login Name*, and *E-Mail*. For more information, see [Configure Allowed Logon Identifiers](configure-allowed-logon-identifiers-3adf1ff.md) .



</td>
<td valign="top">

Path



</td>
</tr>
</table>



### Request Example

```
https://my-tenant.ondemand.com/oauth2/authorize?response_type=id_token&scope=openid&client_id=T000000&state=state&nonce=m-0G6_FaS3Kg&redirect_uri=https://example.com&login_hint=dona.moore@example.com
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

Additionally provides a URL in the header field Location.

> ### Note:  
> The URL contains `id_token`.
> 
> The `id_token` is in the form of a JWT \(JSON Web Token\) and contains information about the user. The `id_token` is valid for 60 minutes.



</td>
</tr>
<tr>
<td valign="top">

400



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
https://www.example.com/#id_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.ey
JhdWQiOiIxMmEzNGI1Yy02ZDc4LTllMWYtZzM0NS02N2g4OWlqa2wxMjMiLCJzdWIiOiJQMTIzNDU2Iiw
ibWFpbCI6ImRvbmEubW9vcmVAZXhhbXBsZS5jb20iLCJpc3MiOiJodHRwczovL215LXRlbmFudC5hY2Nv
dW50cy5vbmRlbWFuZC5jb20iLCJsYXN0X25hbWUiOiJNb29yZSIsInNhcF91aWQiOiIxMjM0NTZhYmM3Z
GU4LWZnaGktOTEyMy1qNDU2LTc4OTEya2wzNG01NiIsImV4cCI6MTU4ODAxODkyNSwiaWF0IjoxNTg4MD
EzNzYwLCJmaXJzdF9uYW1lIjoiRG9uYSIsImp0aSI6IjM4ZTQyMzMwLWRlN2EtNDEzMC1hM2ExLWI1ODJ
iNTI4ZGE5OCJ9.-LSwBN2WSqnnqSkzSbg9iRmtAMR4moU5TpE40mX0Umw&state=state&token_type=Bearer
```

 

**Related Information**  


[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

